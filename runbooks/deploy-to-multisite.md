---
category: Runbooks
expires: 2023-01-31
---

# Deploy steps (on multisite)

## Required

* Github JOTW Dev access
* AWS access
* CircleCi Access
* You'll also need to be connected to the VPN.

## Phases

This assumes this is a code deployment for a theme (Hale) or plugin that the team supports/manages. If deploying an update to a  thrid party theme/plugin skip to Phase III

### Phase I - Create a new release of theme/plugin on github
1. Create a new branch locally of the theme/plugin repo and commit the code changes to this branch. Make sure to update/bump the version number in plugin/theme files.

2. Push the new branch up to github and raise a Pull Request to merge these changes into the main branch.

3. Once the Pull Request has been approved merge it.

4. Go to the releases section in theme/plugin git repo and draft a new release

5. In the draft release form enter the following:
- Tag version - this should be the latest version number of the theme/plugin (the same as updated in the files)
- Release Title - a short title of what has been changed e.g name of new feature or Bug Fix. 
- Release describe - create a list of all the changes/ new features /bug fixes that will be released

6. Publish the release

### Phase II - Update Theme/Plugin Composer repo

1. Login to [CirleCi](https://circleci.com/vcs-authorize/)

2. Go to the CircleCi dashboard to view all pipelines. 

3. Find the the pipeline `pp-satis-config` and rerun the workflow from the start using the action button. 

4. Once this has complete (should only take a few minutes) the status should change from running to success 

5. Check the latest release of the theme/plugin is in the [Composer repo](https://composer.wp.dsd.io/). You will need to be on the VPN to see this.


### Phase III - Update Multisite to bring in latest theme/plugin

1. Make sure you are on the VPN

1. Use the terminal tool to go to the root folder of the multisite. 

2. Switch to master branch (if not already on) and git pull any latest changes down.

3. Create and switch to new a branch from master to push the latest theme/plugin updates to.

4. In terminal (at the root folder of the multisite). run `composer update`

5. This will go through every package listed in the `composer.json` file and update where needed. Watch as it is doing this as other themes/plugins or even Wordpress may be updated.

6. Run `git status`. The `composer.lock` should have been modified. 

7. Spin up the Multisite and test locally the latest changes and to make sure there are no issues from the update.

8. Commit the changes to `composer.lock` to the update branch and push the branch to github

9. Raise a Pull Request to merge the changes to master branch

10. Once the Pull Request has been approved merge it. 

11. This will now trigger a rebuild of the multisite on AWS


### Phase IV - Test and Push the updates through the pipeline

1. Login to the [AWS Console](https://aws.amazon.com/console/) 

2. Go to CodePipeline section in AWS console.

3. Find the multisite pipeline eg. `jotwpublic` (Make sure your in the right region). Click its name to show the full pipeline.

4. This pipeline has the following stages:
- Source - The git repos it uses to build the multisite
- Build - The process the builds the latest image to push to the environments.
- DeployDev - The Dev Environment
- DeployStaging - The Staging Environment
- DeployProduction - The Production Environment

5. Since a change has been pushed to the master branch of the multisite github repo the build stage should be running

6. Once the build has finished the build stage will be its status will updated to `Succeeded` and then it will deploy the build to the dev environment 

7. Once the build has been deployed the DeployDev stage status will also be updated to `Succeeded`

8. Check dev environment

9. If no issues with the dev environment click the `Review` button on the DeployStaging stage then on the popup window click the `Approve` button. This will then deploy the build to staging.

10. Once the build has been deployed to staging its status will be updated to `Succeeded` 

11. Test staging environment e.g. test new bug fixes, features. Make note/list of any content/setting changes that will need to be done  once the updates go to production.

12. Schedule go live of new updates

13. When ready to deploy to production click the `Review` button on the DeployProduction stage then on the popup window click the `Approve` button.  This will then deploy the build to production.

14. Once the build has been deployed to production its status will be updated to `Succeeded` 

15. Check the production site that all updates are working as expected.


