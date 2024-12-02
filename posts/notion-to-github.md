# How I Changed from Notion to GitHub User Content

## The Context

I had just finished implementing my RSS page on the site ([as mentioned in the previous post](https://dailycodes.dev/posts/how-i-implemented-a-rss-feed)), and I was really happy with the results. Sure, the load time isn’t great, but that’s a limitation of RSS feeds (I think). I pull the feeds from various sources, each implementing RSS differently, so I can’t control how many items (episodes) I get at once.

However, I was never satisfied with how I handled the posts.  
Notion’s docs didn’t help much with parsing the blocks, the performance was okay-ish, but most importantly, I had stopped using Notion altogether. These days, I only log in to fix something in my posts when absolutely necessary. So, I started looking for alternatives (and yes, I even considered using a NoSQL database to save the posts—Honestly, I’m still not sure what made me think that was a good idea).

## The Thinking

Then it hit me: why not handle it the same way I did with the RSS feed?  
I’ve already talked about this in my [RSS](https://dailycodes.dev/posts/how-i-implemented-a-rss-feed) post, so feel free to check it out for more details (see what I did there? :D).
## The process

But my minimum requisites are:
 - A visual editor (i already code all the day i dont want the post to be more code), 
 - Dont  manually add them to the site
 - Need to be markdown
 - Free

The solution for all the questions are [Obsidian](https://obsidian.md/) using the [obsidian git](https://github.com/Vinzent03/obsidian-git) plugin.
To me Obsidian is a extension of my mind i personalize it whit plugins to do what i want and to look the way i want with themes. 
Since they will be markdown the files are very small in size so why not use the biggest text hosting plataform, Github! 
The git plugin allow us to sync the Obsidian vault with a git repository so all the 4 requisites are check now, i just need a way to fetch the post from my private repository.

Lucky  to us github provide a endpoint to acess the raw files of any repo in this url `raw.githubusercontent.com/${user}/${repo}/${branch}/${file-path}`

I how i have said i done the same way of the RSS but to summarize, I created a JSON file structured like this:

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
]  
```

I use this file to display featured posts on the homepage. For now, I display all of them since there aren’t too many yet, but as the number grows, I’ll add the same kind of tags logic I implemented for the RSS feed.

To parse the content, I use `react-markdown` to convert the markdown into React components and `gray-matter` to parse the post properties written like this:  
`--- prop: value ---`
