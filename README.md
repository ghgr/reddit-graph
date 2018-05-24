Reddit communities -called subreddits- often link in their description to other similar themed communities. This description is often free text, but with a little bit of regex one can reliably extract the name of subreddits (mostly in the form */r/<subreddit_name>*, but also */r/<subreddit_name>+<subreddit_name>+<subreddit_name>*... ).

As a fun one-day project I started from /r/nsfw, and *recursively* scraped the names of similar subreddits, to see what came. I was expecting something like 30 or 40 communities, and to plot them with matplotlib. Well... I got over *50 thousand* nodes. I scraped the data with PRAW, a Python wrapper for the Reddit API. The data was loaded into [Gephi](https://gephi.org), and finally exported as an interactive website with [gexf-js](https://github.com/raphv/gexf-js). For a moment I though I was going to crawl every existing subreddit, but this dataset (all subreddits that are reachable as 'related communities' starting from */r/nsfw*) only represents less than 5% of the total subreddits.

The size of each node (each subreddit) is proportional to the logarithm of the number of incoming referrals.

You can view the graph at [https://ghgr.github.io/reddit-graph/](https://ghgr.github.io/reddit-graph/). This graph is SFW, since it's text-only, and the NSFW words are located in the bottom half (more or less, it's interesting the gradient from "clearly NSFW" to "somewhat NSFW", to "maybe SFW", to "obviously SFW, like /r/askhistorians").

You can direcly go to a node by using the search field in the top bar.

WARNING: It takes around 2 minutes to load, and in the meantime the tab might freeze. After that it should work smoothly.
