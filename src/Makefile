###
### Makefile for building and pushing site
###

GITHUB_PAGES_BRANCH=gh-pages
THEME = seminar

MARKDOWN = python3 -m markdown

html:
	hugo --theme=$(THEME)

develop:
	sleep 1 && echo "Opening local browser..." &&  open http://localhost:1313 &
	hugo server --theme=$(THEME) --buildDrafts --watch

github: html
	cp -r ./docs ./public/
	cp -r ./images ./public/
	cp -r ./public/* ../
	rm -r ./public
	git add -A :/; git commit -m "Rebuilt site" ; git push

.PHONY: html clean develop
