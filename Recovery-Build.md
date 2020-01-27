## Recovery Build

We release a recovery build with a handful of critical fixes and translation updates a few days after a release. The candidate fixes are reviewed by the development team and are assigned to the recovery milestone. We want to be restrictive about the included candidates. The mindset is "we will lose users if we do not include the fix". Here are some examples:
- data loss
- a regression that users complain loudly about in issues or twitter
- a significant performance regressions
- an issue that impacts many users as indicated by telemetry data
- an embarrassing UI glitch
- critical security fixes
- an issue that impacts extensions or is an API regression

#### Check list
- [ ] Create a milestone `<Month> Recovery <year>` **owner**
- [ ] Bump the version number **owner**
- [ ] Include an issue 'update translations' **owner**
- [ ] Assign candidate issues to the recovery milestone **team**
- [ ] Review the `candidate` issues, and if they pass the review assign them to the recovery milestone **team**
- [ ] All `candidate` fixes are peer reviewed and pushed to `master` and then cherry-picked into the release branch **team**
- [ ] Initiate `insiders` build from `master`
- [ ] Issues are tested in the `insiders` **team**
- [ ] Build `stable` for all platforms from release branch **owner**
- [ ] Make rpm signing request **@Tyriar**
- [ ] Issues are verified on `stable` build and the `verified` label is added **owner**
- [ ] Check `https://github.com/Microsoft/vscode/compare/release/<x.y>` to ensure no other commits have been made in the release branch **owner**
- [ ] Update the release notes and include a link to a query for the fixed issues **@gregvanl**
- [Smoketest](https://github.com/Microsoft/vscode/wiki/Smoke-Test) stable bits  (⚠️ MUST run with `--stable-build` argument ⚠️ )
  - [ ] Windows - **owner**
  - [ ] OS X - **owner**
  - [ ] Linux - **owner**
- [ ] Sanity check of installable bits
  - [ ] Windows 32 bit **owner**
    - [ ] signed installer 32-bit
    - [ ] signed user installer 32-bit
    - [ ] zip 32-bit
  - [ ] Windows 64 bit **owner**
    - [ ] signed installer 64-bit
    - [ ] signed user installer 64-bit
    - [ ] zip 64-bit
  - [ ] OS X - **owner**
  - [ ] Linux
    - [ ] deb package 64-bit **owner**
    - [ ] rpm package 64-bit **owner**
    - [ ] archives **owner**
  - [ ] Server ([instructions](https://github.com/microsoft/vscode-remote-release/wiki/Sanity-Check-VS-Code-Servers)) **owner**
- [ ] Publish website **@gregvanl**
- [ ] Publish stable build **owner**
- [ ] Publish rpm to repository manually **@Tyriar**
- [ ] Add a git tag to `HEAD` of `release/<x.y>` in format `x.y.z`