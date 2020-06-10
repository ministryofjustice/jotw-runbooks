---
category: Runbooks
expires: 2021-01-31
---

# Run security updates

## Required

* Up-to-date master branch - make sure you've run `git pull`!
* Accounts on dev, staging and prod for the site you're updating.
* You'll also need to be connected to the VPN.

## Instructions

You'll need to update both the PHP packages via Composer, and the NPM modules, so this is a two-step process.

### Composer updates

Composer manages the PHP packages, WordPress version and plugin updates.

1. Check in the `composer.json` file for any that don’t have `*` next to them. For any that don’t, ask the team if it needs to be a `*`
2. Run `composer update`
3. Run `git diff` to double check that they ran
4. Run `make build` then `make run` to check that it still builds.
5. Log into the dashboard and check for any bugs.
6. Check that these new plugin versions are present in the dashboard (sometimes an old Docker image gets stored and used in the build process)

Some general notes:
* If the package has a `*` next to it in the `composer.lock` file, it’ll automatically update when you run `composer update`.
If the package has a number next to it instead of a star, it won’t.
* If you run the above steps and log into the dashboard and see WordPress asking you to still update some plugins, check if they’re managed by Satis. We have some plugins that require licenses, or were custom built, and so we control their versions in our team. [View these plugins and their set versions](https://composer.wp.dsd.io/)
* If you’ve tried the above and you’re still having issues, delete your `composer.lock`, delete the `/vendor/` folder, run `composer clearcache` before trying again.


### NPM updates

NPM manages node package modules that are in the theme. These do tasks related to building the front end, like compiling assets.

To update these, run the following steps:

1. Run `npm install` to make sure everything is there
2. Run `npm update`
3. Next, run `npm outdated` to see if any haven’t updated yet. If there are any that haven't, copy the most recent version number shown in the terminal, and manually add it to the `package-lock.json` file and re-run `npm install`.
4. Run `npm audit fix` to see if that fixes anything else that outstanding
5. Rerun `npm audit` to double check they fixes ran. If they didn't, delete the `package-lock.json` and `node_modules/` folder and repeat steps 1-4.
5. Rerun `npm run watch` in the theme folder, to check everything builds
6. Have a look at the front end of the application to check that everything is okay.

General notes:
* Sometimes `npm audit fix` will raise issues with dependencies of dependencies, which can go several levels deep. This is quite hard to address without switching out the package that depends on them. If you come across anything like this that has a high level of security threat/vulnerability, raise it with the team.
