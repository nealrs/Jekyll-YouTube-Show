## Jekyll-YouTube-Show

Create an responsive landing page and iTunes compatible feeds for your YouTube show. 

(podcast landing page and iTunes feed generator)

[Demo landing page my show, The Commit](http://commit.devpost.com) and [Video feed](http://commit.devpost.com/video.xml)

### Credits

I forked and used a lot of code from [Rishat Muhametshin](https://github.com/taxigy)'s [itunes-jekyll-template](https://github.com/taxigy/itunes-jekyll-template) to build this out. 

Holly Tiwari, from Devpost, designed the original Commit landing page using Foundation, drew the logo, and tons more.

## Ok, so I clone this and then what?

In a nutshell, you need to upload your media somewhere, edit a bunch of config stuff so it matches your podcast, create a 'post' for each of your episodes, push the site live, and then submit your feeds to iTunes. 

Step by step:

1. Install the `jekyll` and the `jekyll-paginate` gems and create a new `gh-pages` branch.

2. Setup an s3 bucket to host all your media files. 
	- For the video feed, these will be the same mp4 files you uploaded to YouTube. 
	- For the (optional) audio feed, you'll need to extract the audio track into an mp3.
	- Set permissions on the bucket so that anyone can read/view the files.

3. Create `/video`, `/audio`, and `/img` folders on s3.

4. Upload all your media files to the appropriate folder. I put my podcast logo/art in `/img`. Additionally, note down the following in a spreadsheet for each one: 

	- Filename
	- Episode Title
	- Episode number
	- Release date
	- File size (in bytes)
	- Duration (hh:mm:ss)
	- Show notes / links etc.

5. Open up `_config.yml` and change all the info to match your podcast. Super easy, right?

6. Start a local Jekyll server by running `jekyll s` from the CLI in your repo and navigating to [localhost:4000](http://localhost:4000)

7. Open up `_includes/head.html` and change all the social / meta tags, Google Analytics id, title, favicons, etc. to match your podcast. If you don't use GA, just comment out that block.

8. Create a copy of `_posts/_posttemplate.md` for every episode of your show, name it accordingly: `yyyy-mm-dd-ep#` (eg 2016-03-03-31.md), and populate the details you wrote down in step 3.

9. Preview your landing page and feeds at [localhost:4000](localhost:4000) and [localhost:4000/video.xml](localhost:4000/video.xml). If you see issues, fix them! **BTW**, by default, the page is limited to the latest 7 episodes. That's because this is a landing page with a CTA to subscribe, not an archive. 

10. Commit your edits, push them to GitHub or generate upload them to your server, check that they are live, and then validate your feeds at http://podba.se/validate.

11. If you're hosting your feed/site on GitHub with a custom domain, you must edit the `CNAME` file as well and push everything to `gh-pages` -- not master! If not, delete `CNAME`.

12. Once your video feed validates, go to [FeedBurner](http://feedburder.com), burn the feed, turn on all the podcast stat features, and write down the URL. This is the URL you'll submit to iTunes when you setup your podcast. **FYI** if you're creating both audio & video feeds, you'll need to submit them to iTunes as separate podcasts. 

13. Open up `_layouts/default.html` and update the show description, YouTube subscription link, iTunes mirror feed link, and watch more episodes on YouTube link. You can find the mirror feed link in the settings for your podcast submission. 

14. Save, commit, and push up any more edits.

15. To add a new episode, repeat steps 8 and 14.

Once you submit your podcast, Apple will take ~ 48 hours to review and approve it. Once they do, you'll be able to search for and subscribe to it in iTunes or your favorite podcast catcher.

Daassssss it!