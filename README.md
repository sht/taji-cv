# Awesome markdown CV

Awesome markdown CV for your outstanding job application.

Every platform has their own way to handle markdown syntax. This CV supports [github flavoured markdown](https://github.github.com/gfm/). 

## What will you fine here?
This was the solution I thought to make my own CV in a simple and readable template that is semantic and easy to change.

## Why markdown?

It has always been tough for me to maintain and update my CV in doc format. I thought to leverage markdown format for this. Markdown varies with each platform as I mentioned earlier. I've been using md on [joplin](https://github.com/laurent22/joplin), [Intellij](https://github.com/JetBrains/intellij-community), [sublime](https://github.com/SublimeText-Markdown/MarkdownEditing), etc for various documentation purposes. It's easy to be organised (to-do, bookmarks, notes, etc) with an application which support markdown. I personally liked [joplin](https://github.com/laurent22/joplin), I can convert md to PDF directly there without any additional 3rd party dependency and hustle.

## How to use

You are free to take my `cv.md` file and modify it in any IDE to create your own resume. You can also fork this repo and make changes directly in `cv.md` file.

Once changes done:

We can directly change `cv.md`to PDF with the help of pandoc i.e. `pandoc cv.md -f gfm -o cv.pdf`

But pandoc uses the default PDF template and it won't be beautiful. To make simple but beautiful PDF, we first have to convert `cv.md` to `cv.html`. So: 

- Go to: [https://stackedit.io/app](https://stackedit.io/app) and insert raw content of `cv.md` there.
- Export it as 'Styled HTML'. 
<br>

**Simple way to convert to PDF:**

- Open this html file offline in any browser and `Ctrl+P` to pop up print page window. 
    - Uncheck 'Header and Footer' option and save file as PDF

**Geek way to convert to PDF:**

`pandoc cv.html -o cv.pdf`

or

`pandoc cv.md -f gfm -o cv.pdf`