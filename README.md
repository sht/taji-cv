## How to Use

#### Requirements

A full TeX distribution is assumed.  [Various distributions for different operating systems (Windows, Mac, \*nix) are available](http://tex.stackexchange.com/q/55437) but TeX Live is recommended.
You can [install TeX from upstream](http://tex.stackexchange.com/q/1092) (recommended; most up-to-date) or use `sudo apt-get install texlive-full` if you really want that.  (It's generally a few years behind.)

#### Usage

At a command prompt, run

```bash
$ xelatex {your-cv}.tex
```

This should result in the creation of ``{your-cv}.pdf``

or leverage ci.yml script:

```
compile_pdf:
  stage: build
  image: thomasweise/texlive  # use a Docker image for LaTeX from https://hub.docker.com/
  script: xelatex cv.tex  # build the pdf just as you would on your computer
  artifacts:
    paths: 
      - cv.pdf  # instruct GitLab to keep the cv.pdf file

pages:
  stage: deploy
  script:
    - mkdir public  # create a folder called public
    - cp cv.pdf public  # copy the pdf file into the public folder
  artifacts:
    paths: 
      - public  # instruct GitLab to keep the public folder
  except:
    - master  # Only for the master branch 


```

## Credit

[**LaTeX**](http://www.latex-project.org) is a fantastic typesetting program that a lot of people use these days, especially the math and computer science people in academia.

[**LaTeX FontAwesome**](https://github.com/furl/latex-fontawesome) is bindings for FontAwesome icons to be used in XeLaTeX.

[**Roboto**](https://github.com/google/roboto) is the default font on Android and ChromeOS, and the recommended font for Google’s visual language, Material Design.

[**Source Sans Pro**](https://github.com/adobe-fonts/source-sans-pro) is a set of OpenType fonts that have been designed to work well in user interface (UI) environments.


## Contact

You are free to take my `.tex` file and modify it to create your own cv. Please don't use my cv for anything else without my permission, though!

Good luck!