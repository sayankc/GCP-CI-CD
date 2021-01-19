## About the repo branch
This is one sample repo to protopyte how anything can be executed as `docker run` in **Google cloud build**. 

Refer the documentations

- https://cloud.google.com/cloud-build/docs/build-config
- https://cloud.google.com/sdk/gcloud/reference/builds/submit

## About the code
Code sample has one jmeter performance script with two variations.
1. only jmx file and test data
2. mavenized version of same jmeter project with error % validation
3. the pipeline will demonstrate execution of the same and storage it in **Google cloud bucket** named _skc_bkt_1_ .

## How to Run
- Download google cloud SDK
- Optionaliy save the same repo in google cloud

```
gcloud init
gcloud info
gcloud source repos clone gcp-sample-1 --project=gcp-workshop-trial
##save the cloudbuild.yml as google cloud build pipeline.
git add . & git commit -m "push 25" & git push -u origin master

#create storage bucket ( onetime activity)
gsutil mb -b on -l europe-west1 gs://skc_bkt_1/


```

- trigger the pipeline via 
    - code push 
    - Manually 
    - via google cloud SDK (using following command).
    
_Note: You can control any run time value via substitutions_
```
gcloud builds submit --config=cloudbuild.yaml --substitutions=_PRJ="v5.4"
```

- Add Public access to the storage bucket ( Not Secure)
```
gsutil iam ch allUsers:objectViewer gs://skc_bkt_1/
```

- Remove public access 
```
gsutil iam ch -d allUsers:objectViewer gs://skc_bkt_1/
```
- Delete the bucket
```
gsutil rm -r gs://skc_bkt_1/
```

