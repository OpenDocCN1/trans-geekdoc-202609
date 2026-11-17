```
29.   - docker push $REPOSITORY_URI:latest
30.   - docker push $REPOSITORY_URI:$IMAGE_TAG
31.   - echo Writing container image definitions file...
32.   - printf '[{"name":"mlapp-cicd","imageUri":"%s"}]'
   $REPOSITORY_URI:$IMAGE_TAG > imagedefinitions.json
```

```
33.reports:
34.   pytest_reports:
35.     files:
36.       - Prediction_test_report.xml
37.       - API_test_report.xml
38.     base-directory: pytest_reports/
39.     file-format: JUNITXML
40. artifacts:
41.     files: imagedefinitions.json
```

In the preceding file, mainly three supported builder images are used.

You can see, python:3.7 is the publicly available image used for testing the code using tox. If any image is to be used from the Docker Hub, then simply provide the image name in single quotes. However, if an image is from other registries, then the full registry path needs to be specified in single quotes. The args field of a build phase accepts a list of arguments and passes them to the image referenced by the name field.

To create a build, CodeBuild is used. Search and select CodeBuild from developer tools and choose Build projects from the Build section. Click on the Create build project button to create a new one. First off, under the Project configuration, provide the project name.