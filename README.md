# CS 161 Template Website

A course website template used by various large upper-division CS courses at UC Berkeley, including: [CS 161](https://cs161.org), [CS 168](https://cs168.io), [CS 188](https://inst.eecs.berkeley.edu/~cs188), [CS 61B](https://datastructur.es), and others.

The template is built on Just the Docs (https://just-the-docs.com), so check out their documentation for features such as [callouts](https://just-the-docs.com/docs/configuration/#callouts), [ordering pages in the sidebar](https://just-the-docs.com/docs/navigation/main/order/), [Markdown syntax](https://just-the-docs.com/docs/index-test/), etc. 


## Creating Repo

### Recommended: From Template

We suggest [creating a new repository from this template](https://docs.github.com/en/repositories/creating-and-managing-repositories/creating-a-repository-from-a-template) every semester, since the template is being actively maintained for accessibility.

Then, you can copy over any relevant files from your previous semester's repo into the newly-created template.


### Not Recommended: From Previous Semester

> [!WARNING]  
> This method may involve resolving complicated merge conflicts. If you do not have a good understanding of Git, we recommend using the method above.

If you instead choose to copy the previous semester's repo, then you'll need to take any updates to this template repo, and *manually copy those updates into your own repo*.
- Clone the previous semester's repo
- Rename the folder (e.g. from `fa24-website` to `sp25-website`)
- Delete the `.git` folder, e.g. `rm -rf .git`
- *Delete all bulky files from the repo*, we don't need those clogging up the Git history. Look out for big PDFs like lecture slides, discussion worksheets, staff photos etc.
- Create a new Github repo
  - On your Github organization page, click *New*
  - *Repository name*: `sp25-website` (or whatever naming convention you use)
  - *Description*: [https://inst.eecs.berkeley.edu/~cs188/sp25](https://inst.eecs.berkeley.edu/~cs188/sp25) (or whatever your URL will be)
  - *Private* (not Public)
  - Leave everything else untouched => *Create repository*
  - Back in your terminal, follow the steps under *create a new repository on the command line* while cd'd into your `sp25-website` repo. Should be init, add, commit, branch, remote add, and push.
- Manually copy all new updates from the `course-site-template` repo into your newly-created repo.


### Configuring New Repo

Recommended: Set dummy-proof PR rules.
- On the Github repo page, to go *Settings*
- *Pull Requests*:
 - *Allow merge commits*: `false`
 - *Allow squash merging*: `true`
 - *Default commit message*: Pull request title (others are also ok)
 - *Allow rebase merging*: `false`
- *Automatically delete head branches*: `true`
- Should auto-save

Once you've created the new website, you should mark the old website as outdated. Assuming the old website also uses this template:
- Go to `_config.yml` in the old website repo
- Set `outdated: true`


## Installation

### Jekyll

Anybody updating the website should have [Jekyll installed](https://jekyllrb.com/docs/installation/) so that you can check that the site builds locally before you push any changes.

After installation, `cd` into the website repo and run `bundle exec jekyll serve` to build the website locally. The local website will automatically re-build every time you edit files.


### Pushing updates

> [!IMPORTANT]
> You should *always build locally* and check before pushing any changes. Don't be that person who pushes broken code to production.

> [!IMPORTANT]
> You should always [use pull requests](https://github.blog/developer-skills/github/beginners-guide-to-github-creating-a-pull-request/#creating-your-pull-request) for non-trivial updates. Don't push potentially-breaking changes directly to main.

To update the website, just push to this repo, and the website will automatically build and update in around a minute.

Always remember to **build locally first** with `bundle exec jekyll serve` to make sure that your edits work before committing and pushing them.

To keep the repo clean, **please tag your commit messages** by adding an assignment tag at the beginning. Examples:
- `[disc02] release`
- `[hw02] add electronic hw`
- `[proj1] fix typo in spec`


### Custom domain deploy

TODO - use Github Actions to deploy to a custom URL like https://sp25.cs161.org.


### inst.eecs deploy

For UC Berkeley classes only: Refer to this [GitHub gist](https://gist.github.com/ashmchiu/797f80d9d4c1d674b9868c0a01b633c0) for information on setting up the website to deploy on an inst.eecs URL like https://inst.eecs.berkeley.edu/~cs188/sp25.


### Scheduling assignment release

For assignment releases, we recommend the GitHub workflow, [gr2m/merge-schedule-action](https://github.com/gr2m/merge-schedule-action). The configuration that they provide in the "Usage" section of their documentation is what we recommend. Make sure to update your timezone to reflect the timezone you are teaching the course in.

The workflow activates when a PR is made or edited, and checks if the last line includes the `/schedule` command. If so, it will attempt to merge the PR at the time specified after the command. The command accepts:
 - A date in YYYY-MM-DD format (2025-06-15), which will merge at midnight in the timezone you specify.
 - A timezone-sensitive `ISO 8601` date string (2025-06-15T09:00:00.000Z)
 - Nothing, which will merge the next time the cron job is ran.

For example, to schedule a PR to merge on June 16th at midnight in your specified timezone, the last line of a PR should be `/schedule 2025-06-16`. The workflow will add a comment to your PR confirming that it is scheduled.

## Start of Semester Setup

### Configuration

> [!NOTE]
> If you've used this template before, you can check your previous semester's config and syllabus files to see how they were filled out last time.

Go to `_config.yml` and follow instructions in that file to update all relevant fields. (Note: You will need to re-run `bundle exec jekyll serve` every time you update this file.)

Next, go to `_data/syllabus.yml` and follow instructions in that file to update all relevant fields.


### Calendar

The calendar page pulls and displays events from a Google Calendar.

Set up your calendar:
- Go to https://calendar.google.com
- Sign in. For UC Berkeley classes, you should sign in as your class [SPA account](https://calnet.berkeley.edu/calnet-departments/special-purpose-accounts-spa), e.g. cs188@berkeley.edu, so that multiple TAs can edit the calendar.
- Click `+` next to *Other calendars* in the right sidebar --> *Create new calendar*
- *Name*: `[CS188 SP25] Website` or similar
- *Description*: blank is fine
- *Time zone*: `GMT-07:00 Pacific Time - Los Angeles`
- Click *Create calendar*

Now go to `_data/calendar.yml`:
- Follow the steps in that file to fill out the four Google Calendar fields.
- Follow the steps in that file to update `remove_prefix`.
- You probably do not need to touch `categories`.

Populate some Google Calendar events to check that it works (using lecture below as an example):
- Back to https://calendar.google.com
- Uncheck everything except `[CS188 SP25] Website` in the sidebar
- Create the lecture calendar event
- *Title*: `[CS188 SP25] Lecture`
- *Location*: `Dwinelle 155` or whatever the room on https://classes.berkeley.edu is
- Note: You want *Location* filled in, but *Room* can be blank
- Click *More options*
- Replace *Does not repeat* with *Custom*
- Fill in your lecture times, e.g. `every Tu/Th`, ending on `May 5, 2025`
- Save, and see if the event appears on the website (if not, you did something wrong, so go back and fix it)

Once the calendar is set up, you can populate Google Calendar with events throughout the semester, and they'll sync on the website.


### Staff

Updating the staff page happens in the `_staffers` folder. Make one `.md` file per member of course staff, following the template provided.

The documentation (and some extra configuration) lives in `_data/staff.yml`.

**Compressing staff images**: Please don't put enormous 4096x4096 staff images in the website repo and force staff/students to load those every time.

> [!WARNING]
> Skipping this step may lead to substantially longer load times, and a much larger Git repository.

Our recommended way to compress images is with the script below, which relies on [ImageMagick](https://imagemagick.org/), a command-line image manipulation program which supports Windows, MacOS, and Linux. It automatically resizes each image, and saves them as a `.webp`. If you do not wish to use ImageMagick, the same thing can be accomplished manually using [GIMP](https://gimp.org), Photoshop, or any other image editor.

There is a different script for each common shell. If you do not know which shell you are using, you can type `echo $0` into your terminal to find out.

Do this before committing them into the repo (otherwise the large image just ends up in the Git history and defeats the point). Make sure to remove the old files, since the command does not do this for you.

<details open>
  <summary>BASH Script</summary>

  ```shell
  shopt -s nullglob
  for i in *.{png,PNG,gif,GIF,heic,HEIC,jpg,JPG,jpeg,JPEG,jfif,JFIF}; do magick "$i" "${i%.*}.webp"; done
  for i in *.{WEBP}; do mv "$i" "${i%.*}.webp"; done
  mogrify -resize '512x512^>' -gravity center -crop '512x512+0+0' -strip *.webp
  shopt -u nullglob
  ```
</details>

<details>
  <summary>ZSH Script</summary>

  ```shell
  setopt CSH_NULL_GLOB
  for i in *.{png,PNG,gif,GIF,heic,HEIC,jpg,JPG,jpeg,JPEG,jfif,JFIF}; do convert "$i" "${i%.*}.webp"; done
  for i in *.{WEBP}; do mv "$i" "${i%.*}.webp"; done
  mogrify -resize '512x512^>' -gravity center -crop '512x512+0+0' -strip *.webp
  setopt NOMATCH
  ```
</details>

<details>
  <summary>Other</summary>

  If you are using a shell like `fish` which does not support complicated globbing, your best bet is just to break into bash temporarily.
  ```shell
  bash -O nullglob -c "for i in *.{png,PNG,gif,GIF,heic,HEIC,jpg,JPG,jpeg,JPEG,jfif,JFIF}; do convert '$i' '${i%.*}.webp'; done"
  bash -O nullglob -c "for i in *.{WEBP}; do mv '$i' '${i%.*}.webp'; done"
  mogrify -resize '512x512^>' -gravity center -crop '512x512+0+0' -strip *.webp
  ```
</details>


## Updates Throughout Semester

### Syllabus

To edit the syllabus (the big table on the homepage), follow the instructions in the relevant file. No other files should need to be edited.
- `_data/lectures.yml`
- `_data/readings.yml`
- `_data/homeworks.yml`
- `_data/projects.yml`
- `_data/labs.yml`


### Weekly Announcements

To add a new weekly announcement, just add a new Markdown file in `_announcements`. See the sample files in that folder for examples.

The homepage defaults to showing the most recent announcement.


### Templating

Jekyll allows you to write Markdown pages that reference variables defined in `_data` files.

For example, in `proj1_assignment.yml` we listed assignment-specific attributes, and used them in `proj1/index.md`. This allows you to re-use project specs across semesters, without worrying that you're forgetting to update a submission link or due date.

Another example of data is in `_data/exams.yml`, which lists exam dates that get used in `exam.md`.

Another example of data is in `_data/faqs.yml`, which lists next-semester dates that get used in `resources/faqs.md`.
   

## Customization

> [!WARNING]  
> Some competency in Jekyll and HTML required for this step. We don't recommend attempting this unless you know what you're doing.

If you want to change the layout of the syllabus (the big table on the homepage), you will need to manually edit some more obscure files.


### Syllabus Files

Files used to build the syllabus (each file has more documentation):
- `_includes/lecture.html` has the code for rendering a single box in the "Lectures" column, using a single entry from `_data/lectures.yml`.
- `_includes/readings.html` has the code for rendering a single box in the "Readings" column, using a single entry from `_data/lectures.yml` (lectures and readings share a data file).
- `_includes/discussion.html` has the code for rendering a single box in the "Discussion" column, using a single entry from `_data/discussions.yml`.
- There is just a single piece of code for rendering assignments, used in `_includes/homework.html`, `_includes/lab.html`, and `_includes/project.html`. For simplicity, we suggest keeping these files all identical. Each assignment box is rendered using a single entry from `_data/homeworks.yml`, `_data/labs.html`, and `_data/projects.html`, respectively. The usage of these data files is identical (since the code for rendering all three is the same).
- `_includes/syllabus.html` actually builds the table by using all of the other `_includes` files to build individual boxes, and then putting those boxes together. It also accepts data from `_data/week_extra.yml` (see that file for more documentation).


### Customizing Syllabus

This section some possible changes you might want to perform, and how to implement them.

**Add a separate readings column?** (by default, readings appear in the Lectures column)
- In `_includes/syllabus.html`, uncomment the Readings header and the code for rendering the column (Ctrl+F the word "uncomment" for the two places you need to edit).
- Edit `_data/syllabus.yml` to configure your new Readings column. The config variables are already there, they just go unused by default (when there's no Readings column).

**Add a new assignments column?** (e.g. for labs or vitamins)
- In `_includes/syllabus.html`, uncomment the Labs header and the code for rendering the column (Ctrl+F the word "uncomment" for the two places you need to edit).
- In `_includes/syllabus.html`, you can rename the header you just uncommented - right now it's Labs but it can be whatever else. The other variables can still be called lab, e.g. "lab_element", and they won't show up on the website, so it's probably easiest to leave them unchanged.

**Add a new column for something else? (easier)** (e.g. a second readings column)
> [!CAUTION]
> If you're using `extra` in every cell, you should make sure that the text in each cell is distinct, for accessibility reasons. (e.g. don't make every link say "Slides")
- If you aren't already using the Labs column, the easiest way to add a new column is to repurpose the Labs column for your purposes.
- First, follow the two steps above (in the "Add a new assignments column") section. This enables the Labs column and renames the column header.
- Now, in `labs.yml` (which also doesn't need to be renamed), you can add data to feed into your new column, even if that data isn't an assignment.
- For example, you can use `extra` to put arbitrary Markdown in each cell, use `nonumber` to disable auto-numbering the cells, and use `rowspan` to control the size of each cell. See example below.

```
labs:
  - nonumber: true
    extra: |
      [How to make pancakes](https://www.example1.com)

      [How to make syrup](https://www.example3.com)
    rowspan: 1
  - nonumber: true
    extra: |
      [How to make waffles](https://www.example2.com)
    rowspan: 2
  - nonumber: true
    extra: |
      [How to brownies](https://www.example4.com)
    rowspan: 1
```


**Add a new column for something else? (harder)** (e.g. adding both a Labs and a Vitamins column)
> [!CAUTION]
> You should be manually validating WCAG AA accessibility of your new code. If you're not sure how to do these steps, try the easier approach above.

> [!WARNING]
> Adding too many columns will make the table hard to read, especially on smaller screens (e.g. mobile).
- In `_includes/syllabus.html`, add a new header near the top of the file.
- In `_includes/syllabus.html`, below the headers, initialize new counters, e.g. `vitamin_index`, `vitamin_rowspan`, `vitamin_number`, `default_vitamin_number`.
- In `_includes/syllabus.html`, the second half of the file has mostly-identical codeblocks for rendering each column (e.g. look for "Render the homework column."). Copy-paste this codeblock for the new column in the appropriate place (e.g. if your column is between Homework and Project, then your new codeblock should be between the homework-rendering and project-rendering codeblocks).
- Don't customize the codeblock in `_includes/syllabus.html`. Instead, make a new includes file, e.g. `_includes/vitamin.html`, and write your custom code for rendering a single box here. Look at other files like `_includes/homework.yml` for inspiration.
- Make a new data file, e.g. `_data/vitamins.yml`, for feeding data into your new includes file. Look at other files like `_data/homeworks.yml` for inspiration.


**Rearrange columns?**
- In `_includes/syllabus.html`, reorder the headers near the top of the file.
- In `_includes/syllabus.html`, the second half of the file has mostly-identical codeblocks for rendering each column (e.g. look for "Render the homework column."). Reorder these codeblocks to match your desired order.


**Change the discussion types?** (e.g. add a third type of discussion)
- TODO


**Change the way lectures/discussions are rendered?**
- All the code for rendering a single lecture box and a single discussion box are in `_includes/lecture.html` and `_includes/discussion.html`, so you should only need to modify those two files.


**Change the way assignments are rendered?**
- All the code for rendering a single assignment is in `_includes/homework.html`. For simplicity, the other assignment files (`_includes/project.html` and `_includes/lab.html`) are identical. You should only need to edit these files.
- These files are already made to be fairly extensible (e.g. `parts` for rendering any list of links, and `extra` for any arbitrary Markdown), so you may be able to achieve the desired behavior without changing these HTML files.