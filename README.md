### Preparatioin for test_longGWAS (Do not run this command)
The followings are the command to make this repository. Don't run this command. This is just for the record.
```
git clone https://github.com/hirotaka-i/new_analysis.git test_longGWAS
cd test_longGWAS
rm -rf .git # remove the git history
git clone https://github.com/AMCalejandro/testdata
mv testdata example # default demo command uses "example" folder name
rm -rf example/.git # remove the git history
echo "work" >> .gitignore
echo "files" >> .gitignore
echo ".nextflow" >> .gitignore
git init
```

# Nextflow command to test
```
git clone ~~~.git
cd test_longGWAS
# default
nextflow run michael-ta/longitudinal-GWAS-pipeline -profile standard -r main -resume

# with params
nextflow run michael-ta/longitudinal-GWAS-pipeline \
-params-file params.yml \
-profile standard -r main
```



# Debugging the pipeline
If you need to degub the pipeline, you can fork the repository and modify the code on your local environment. Then run it instead of `Michael-ta/longitudinal-GWAS-pipeline`. The example is shown below.
```
# fork https://github.com/michael-ta/longitudinal-GWAS-pipeline.git on GitHub
# clone the forked repository somewhere outside of the test_longGWAS folder
# git clone YOUR_FORKED_REPOSITORY
# cd YOUR_FORKED_REPOSITORY
# git remote add upstream https://github.com/michael-ta/longitudinal-GWAS-pipeline.git
# git checkout -b some_modification
### do some modification
# git pull upstream main # to get the latest version to prevent conflict
# git push origin some_modification # push the modified version to YOUR_FORKED_REPOSITORY
## Make a pull request on GitHub
```
```
# going back to the test_longGWAS folder
nextflow run PATH_TO_YOUR_FORKED_REPOSITORY/main.nf -params-file params.yml -profile standard
```
nextflow run ../longitudinal-GWAS-pipeline/main.nf -params-file params.yml -profile standard


# Clear the caches
rm .nextflow*
rm -rf work
rm -rf files
