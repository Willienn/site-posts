# How I Changed from Notion to GitHub User Content

## The Context

I was just finished to implement ([as said in the previous post](https://dailycodes.dev/posts/how-i-implemented-a-rss-feed)) my rss page on the site and i was very happy with the results. Yes the load time isn't the best but is a limitation of rss feeds (i think). I get the feeds from diferent sources that use diferent ways of implement it. So i cant control how many eps i get at once.

But i was never happy with the way i done the posts.
Notion docs never help about parsing the blocks, the performance its ok and the most important i stop using notion a long time ago, just entering to fix something in my posts. I start looking for alternatives (and even think in use a no-sql db to save the posts???).

## The Thinking

Until i figure it out, why not do de same way i done with the rss feed ? 
I have already talk about this in my [rss](https://dailycodes.dev/posts/how-i-implemented-a-rss-feed) post so go there to know more (see what i done here?! :D)
But resuming i have create a json file as follows:
```json
export const posts = [
 {
   title: "Post Title",
   url: "https://raw.githubusercontent.com/post/path/in/github",
   image:"https://cdn.com/path/to/post/image",
   slug: "post-slug",
   tags: ["post-tag"],
   updatedAt: "2024-9-29",
 },
]
```

then i parsed the content using  ``react-markdown``

``rehype-raw``

 ``remark-gfm``

 ``gray-matter``