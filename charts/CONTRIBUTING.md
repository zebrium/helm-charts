# Contributing to Zebrium Helm-Charts
Thank you for expressing intrest in contriburing to the Zebrium Internal Helm Charts. Below you will find the general contributing guidelines as well as tools used
throught the process. 

## What belongs here
Any public helm chart maintained by Sciencelogic for the Zebrium Product

## How do I add new charts?
New charts can be added to the charts directory. To start, you can run the following to generate a default templated chart in the [charts directory](charts/): 
```
helm create NAME 
```
Now your chart will be included in all the CICD and tool automation listed below. Once you have finished your chart and are ready to publish, add your chart to the list in the [root readme](../README.md)


## Where are these Charts released too
Charts are released to a github page and stored at charts.zebrium.com.  Releaseing is done through Helm's [chart-releaser](https://github.com/helm/chart-releaser)
## Automation 
This section describes the automation used for testing, doc-generation, and build/publishing of repos. 

### Readme docs generations
README's for each chart are generated from chart metadata using [helm-docs](https://github.com/norwoodj/helm-docs).  This can be controlled by a README.md.gotmpl.  Please see plugin github for more 

### Chart Unit Testing
Charts are unit tested using [helm-unittest](https://github.com/helm-unittest/helm-unittest)

### Liniting
This repo used [chart-testing](https://github.com/helm/chart-testing) for all CICD linting and testing 

### CICD Processes
TODO: Update