---
banner: https://i.imgur.com/5etxlhW.jpg
title: Changing from Notion to GitHub
---
## The Context

I had just finished implementing my RSS page on the site ([as mentioned in the previous post](https://dailycodes.dev/posts/how-i-implemented-a-rss-feed)), and I was really happy with the results. Sure, the load time isn’t great, but that’s just a limitation of RSS feeds (I think). I pull feeds from various sources, each implementing RSS differently, so I can’t control how many items (episodes) I get at once.

However, I was never satisfied with how I handled the posts.  
Notion’s docs didn’t help much with parsing the blocks, the performance was okay-ish, but most importantly, I had stopped using Notion altogether. These days, I only login to fix something in my posts when absolutely necessary. So, I started looking for alternatives (and yes, I even considered using a NoSQL database to save the posts—honestly, no idea why I thought that was a good idea).

## The Thinking

Then it hit me: why not handle it the same way I did with the RSS feed?  
I’ve already talked about this in my [RSS](https://dailycodes.dev/posts/how-i-implemented-a-rss-feed) post, so feel free to check it out for more details (see what I did here? :D).

## The Process

My minimum requirements were:

- A visual editor (I already code all day; I don’t want posts to feel like more coding).
- No manual work to add posts to the site.
- Markdown support.
- Free.

The solution to all these questions was [Obsidian](https://obsidian.md/) with the [Obsidian Git](https://github.com/Vinzent03/obsidian-git) plugin.

For me, Obsidian feels like an extension of my mind. I customize it with plugins to do exactly what I want and make it look the way I like with themes. Since the posts are markdown files, they’re small in size, so I thought, _why not use the biggest text-hosting platform?_ GitHub!

The Git plugin lets us sync the Obsidian vault with a Git repository, so all four requirements are checked. Now I just needed a way to fetch the posts from my private repository.

Luckily for us, GitHub provides an endpoint to access raw files in any repo using this URL:  
`raw.githubusercontent.com/${user}/${repo}/${branch}/${file-path}`.

Now we just fetch the files and process them in the app.

We handle this the same way as RSS. To summarize, I created a JSON file structured like this:

```json
export const posts = [  
  {  
    title: "Post Title",  
    url: "https://raw.githubusercontent.com/post/path/in/github",  
    image: "https://cdn.com/path/to/post/image",  
    slug: "post-slug",  
    tags: ["post-tag"],  
    updatedAt: "2024-9-29"  
  }  
];  
```

I use this file to display featured posts on the homepage. For now, I display all of them since there aren’t too many yet, but as the number grows, I’ll add tag-based filtering, similar to what I did for the RSS feed.

If we need to filter anything, we just take the slug from the URL and do a `posts.filter(slug)`. If we need all the posts, we just use `map()` to get all the metadata we need. For example, I use this for [dynamic metadata](https://nextjs.org/docs/app/building-your-application/optimizing/metadata#dynamic-metadata) and [static params](https://nextjs.org/docs/app/building-your-application/routing/dynamic-routes#generating-static-params):

```javascript
export async function generateMetadata({ params }) {  
  const { slug } = await params;  
  const post = await fetchPost(slug); // just a helper to fetch from github 
  const { data } = matter(post);  
  const { banner, title } = data;  

  return {  
    title,  
    // TODO: Add more fields here  
    openGraph: { images: banner }  
  };  
}  
```

```javascript
export async function generateStaticParams() {  
  return posts.map((post) => ({ slug: post.slug }));  
}  
```

To parse the content, I use `react-markdown` to convert markdown into React components and `gray-matter` to parse post properties written like this:  
`--- prop: value ---`.

There isn’t much code to show because it’s really simple—it’s literally a React component where you pass the markdown. You just set components for each "markdown tag" to style it how you want:

```javascript
const markdownConfig = {  
  remarkPlugins: [remarkGfm],  
  rehypePlugins: [rehypeRaw],  
  components: {  
    h1: Heading1, // My Components  
    h2: Heading2, //  
  }  
};  
```

And that’s it! This is how I’m creating the post you’re reading right now in a simple, lightweight, and free way. :D