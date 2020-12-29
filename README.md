## About the repo branch
This is one sample repo to protopyte how anything can be executed as `docker run` in **Google cloud build**. 

Refer the documentations

- https://cloud.google.com/cloud-build/docs/build-config
- https://cloud.google.com/sdk/gcloud/reference/builds/submit

## About the code
Code sample has one performance script with two variations.
1. only jmx file and test data
2. mavenized version of same jmeter project with error % validation
3. the pipeline will demonstrate execution of the same and storage it in **Google cloud bucket** named _skc_bkt_1_ .

## How to Run
- download google cloud SDK
- Optionaliy save the same repo in google cloud

```
gcloud init
gcloud info
gcloud source repos clone gcp-sample-1 --project=gcp-demo-1
git add . & git commit -m "push 25" & git push -u origin master

```

- save the yml as google cloud build pipeline.
- trigger the pipeline via 
    - code push 
    - Manually 
    - via google cloud SDK (using follow command).
```
gcloud builds submit --config=cloudbuild.yaml --substitutions=_PRJ="v5.4"
```

