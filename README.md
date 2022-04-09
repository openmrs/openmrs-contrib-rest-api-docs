# openmrs-contrib-rest-api-docs

This is the repository for OpenMRS REST API documentation.

The live documentation site can be viewed at [rest.openmrs.org](https://rest.openmrs.org/).

## Contributing to the documentation

OpenMRS documentation is built using [Slate](https://github.com/slatedocs/slate). 
All documentation can be found in the `source/includes/` directory and uses 
[Markdown](https://guides.github.com/features/mastering-markdown/) text format. 

Contributions are welcome!

## Get Started 

Fork this repository in Github and submit the changes via pull requests. If 
you browse to the markdown files in this repository and edit them, GitHub will 
guide you through forking and making a pull request with your suggested changes.

### Build the REST API Documentation locally

Use Git to clone the repository and use Docker to build and serve it (requires pre-installed git and docker).

1. Clone the openmrs-contrib-rest-api-docs repository: 
```
git clone https://github.com/openmrs/openmrs-contrib-rest-api-docs.git
```
2. Start the server
```
docker run --rm --name slate \
  -v "$(pwd)/build:/srv/slate/build" \
  -v "$(pwd)/source/index.html.md:/srv/slate/source/index.html.md" \
  -v "$(pwd)/source/includes:/srv/slate/source/includes" \
  -v "$(pwd)/source/images/logo.png:/srv/slate/source/images/logo.png" \
  -p 4567:4567 slatedocs/slate serve
```

Browse to http://localhost:4567/ and you should see the docs!

### Guide for new PR's

1. Make sure you add the document inside under the `source/includes/` folder 
inside the relevant subfolder.

2. Make sure to follow conventions used in existing markdown files for consistency.

3. New files need to be added to the list of inclusions in 
[`source/includes/info.md`](source/includes/info.md).
