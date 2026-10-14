ANJAANLY WEBSITE FILES

IMPORTANT
These files make the Anjaanly demo website. They do NOT yet connect real strangers to one another. Do not advertise the site as a working live chat until the secure backend, matching, message access rules, reporting, and moderation have been built and tested.

HOW TO UPDATE YOUR GITHUB REPOSITORY ON A PHONE
1. Open your repository: https://github.com/Mahadev1807/Anjaanly
2. Open each existing file: index.html, styles.css, and app.js.
3. Replace the contents with the matching file from this folder. If GitHub's mobile editor is difficult, use the repository's Add file / Upload files option to upload these three files from the ZIP after extracting it. If prompted, confirm replacing the existing files.
4. Commit the changes with the message: Update Anjaanly website files
5. Wait a minute, then open https://mahadev1807.github.io/Anjaanly/ and refresh.

FILES
- index.html: website page structure
- styles.css: website design
- app.js: demo interactions

SUPABASE STATUS
The tables created in Supabase are only the database foundation. Do not create public policies that let every visitor read or edit all chat rooms/messages. A secure server-side matching/message layer and carefully scoped access policies are still required before real chat can go live.

SAFETY BEFORE PUBLIC LAUNCH
Because this is a stranger-chat website, add server-side rate limits, block/report handling, moderation tools, a clear privacy notice, a way to handle abuse reports, and test access controls before allowing real users to chat.
