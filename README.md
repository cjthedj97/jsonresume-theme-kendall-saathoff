# jsonresume-theme-kendall-saathoff

A theme for the [JSONResume](https://github.com/jsonresume/resume-schema) schema, that relies on Bootstrap and FontAwesome, added with some personal flair.

Pulled in the changes from https://github.com/daniel-herink/jsonresume-theme-kendall-herink/ but being that I wanted somehthing sligly different forked off the orignal.

Orignal at https://github.com/LinuxBozo/jsonresume-theme-kendall/

**NOTE**: This supports schema 1.0.0. Some things may be missing or broken if your resume.json is using the older schema.

## Typical Work-Flow

### Install `resumed`

To first use this theme, you will need to install the [`resumed` CLI tool](https://github.com/rbardini/resumed). This is an alternative to the official [JSONResume CLI tool](https://github.com/jsonresume/resume-cli) that is a more modern implementation of the original tool. I prefer it to the JSONResume CLI tool.

Install `resumed` and this theme with:

```
npm install resumed jsonresume-theme-kendall-saathoff
```

### Put Together Your JSON Resume

In order to generate an HTML page of your JSON resume, you will of course need your resume info plugged into the proper schema. Refer to the [JSONResume](https://github.com/jsonresume/resume-schema) repo for more information. You can also call (this assumes that `resumed` is installed in a local location):

```
/path/to/resumed/bin/resume.js init my-resume.json
```

This will create a JSON resume named "my-resume.json" with a number of fields filled out with generic information. You can use this to replace those default JSON values with your own resume details.

### Use Theme with `resumed` to Generate HTML

The handy feature of `resumed` is that when you install it with a theme, it will always default to that theme. All that is required is to call:

```
/path/to/resumed/bin/resume.js render my-resume.json -o my-resume.html
```

This will take your filled-in "my-resume.json" and create the HTML form of the resume named "my-resume.html", using this theme (assuming you installed `resumed` as detailed above).

Refer to `resumed` for the full documentation on its usage.

### Bonus: Render PDF from HTML

After creating or updating your JSON resume and generating the HTML page from it, the next step is to get a PDF of your resume. For this last step, I use Docker (or [podman](https://github.com/containers/podman), if you're familiar with it) to use a headless Chrome browser to print the HTML page to a PDF file.

To generate a slick-looking PDF, with no margins, and limited to one page, I use the docker call:

```
docker run -v "/path/to/jsomeresume/folder:/workspace" pink33n/html-to-pdf --url http://localhost/my-resume.html --pdf my-resume.pdf --no-margins --page-ranges 1
```

This will create a PDF version of your resume named "my-resume.pdf" in the same folder as the "my-resume.html" file. You can drop the `--page-ranges 1` in order to allow for multiple pages for your resume PDF.

Refer to the [pink33n/docker-html-to-pdf](https://github.com/pinkeen/docker-html-to-pdf) for full documentation.

## Why the Changes?

First are concerns about the orignal theme not having receaved fixes in quite some time. Second because the orignal theme doesn't fit what I want, so taking matters into my own hands. See the list below for the changes I have made.

- Removal of the profile picture
- Improving the projects section
- Changed the colors
- Adding a certifications section
- Removing the Language Section
