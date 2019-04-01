# qinren-standard-web
Webpage version of the QinRen standard (via mkdocs)

## Requirement:

[mkdocs](https://www.mkdocs.org/)

## How to run the server of qinren-standard-webpage?

```bash
docs-cn$ mkdocs serve
```

## How to convert the mkdocs server into static webpage?

```bash
docs-cn$ mkdocs build
```

## Structure

```
docs-cn/				# Chinese version of qinren standard
	mkdocs.yml 			# Basic settings for the mkdocs project
	docs/				# All the related sections 
		index.md 		# Main page
		project/		# Standard for project management
			index.md 	# index page for this section
		code/			# Standard for code manangement
			index.md
		application/
		others/	
		img/			# All the related images
	theme/				# The theme for the webpage

```