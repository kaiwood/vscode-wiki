Each iteration closes with an [endgame](https://github.com/Microsoft/vscode/wiki/Development-Process#end-game).

## Duties of the endgame master

> Proactive communication is key to a smooth and successful endgame.

- update iteration plan issue with the endgame schedule (see template below and potentially last month's schedule)
  - ensure each plan item is linked to a test item
- discuss the endgame schedule in Monday's planning call
  - find an endgame buddy in the other lab
  - determine the pool of testers and their availability
- ensure each test item has meaningful content
- assign test items to testers (usually platform specific); ensure fair distribution across testers ([see this example](https://microsoft.sharepoint.com/teams/DD_OTP/_layouts/OneNote.aspx?id=%2Fteams%2FDD_OTP%2FDocuments%2FTicino%2FNotebooks%2FTicino&wd=target%28Sprints.one%7C97CC4DED-1C83-4716-A6D1-C080F036F75D%2FJuneTest%20Load%20Balancer%7CBAABAED7-7FC1-6E47-A901-D2E514241DD6%2F%29))
- communicate test assignments in the `release` slack channel by posting the test item queries ([example query](https://github.com/Microsoft/vscode/issues?q=label%3Atestplan-item+milestone%3A%22June+2016%22+is%3Aclosed))
- communicate end of day progress in the `release` slack by communicating
   - the number of issues filed
   - the number of test items not yet completed ([example query](https://github.com/Microsoft/vscode/issues?q=label%3Atestplan-item+milestone%3A%22June+2016%22+is%3Aclosed))
   - number of issues to be [verified](https://github.com/Microsoft/vscode/wiki/Issue-Tracking#verification)
- assign owners to checklist items for each day (if not owned by the endgame master)
- track progress on test items and checklist items
- adjust schedule, particularly the publishing dates, based on defects found, fixes made, holidays, vacations, etc.

## Schedule Template
- *Month/Day* Code freeze for the endgame
- *Month/Day* Endgame done

##### Monday
- [ ] Code freeze at 5pm PT
- [ ] Ensure we have a green build on all platforms
- [ ] All test items contain sufficiently comprehensive test descriptions by 6pm PT

##### Tuesday
- [ ] Test build starts at 7am CET / 10pm PT on Monday
- [ ] Test plan ready by 8am CET / 11pm PT on Monday
- [ ] Testing

##### Wednesday
- [ ] Testing
- [ ] Remind team members to assign issues that they intend to fix to the July milestone
- [ ] Fixing (self-assigned, milestone assigned)
- [ ] [Verification](https://github.com/Microsoft/vscode/wiki/Issue-Tracking#verification)

##### Thursday
- [ ] Fixing (scrutiny sets in - major bugs only - to be discussed in stand-up meeting, labeled as `candidate`)
- [ ] [Verification](https://github.com/Microsoft/vscode/wiki/Issue-Tracking#verification)
- [ ] Update release notes
   - release notes are collected in a file named *`Major_Minor.md`* in this [repo directory](https://github.com/Microsoft/vscode-docs/blob/vnext/release-notes/)
- [ ] Add/update shrink-wrap files for built-in extensions if needed (see [instructions](https://github.com/Microsoft/vscode/issues/8570#issuecomment-229669456))
- [ ] Update `OSSREADME.json` for built-in extensions based on differences to generated `npm-shrinkwrap.json` files if needed
- [ ] Run [OSS tool](https://github.com/Microsoft/vscode-distro/blob/master/distro-tools/README.md) after merging shrink-wrap findings **@owner**
  - *The LCA review of the ThirdPartyNotices.txt files is not needed anymore*
- [ ] Check new OSS usage is entered into the [OSS registry](https://ossmsft.visualstudio.com/_apps/hub/ms.vss-oss-web.hub-oss) **@owner**

##### Friday
- [ ] Pause scheduled `insider` builds **@zurich**
- Satellite modules/npm packages ready, version updated, smoke tested
  - [ ] vscode **@bpasero**
  - [ ] yo generator **@aeschli**
  - [ ] vsce **@joaomoreno**
  - [ ] node debug **@weinand**
- [ ] Translation input - **@dbaeumer**
- [ ] All issues [verified](https://github.com/Microsoft/vscode/wiki/Issue-Tracking#verification)
- [ ] Fixing (only critical bugs - no string changes)
- [Smoketest](https://github.com/Microsoft/vscode/wiki/Smoke-Test)
  - [ ] Windows - **@owner**
  - [ ] OS X - **@owner**
  - [ ] Linux - **@owner**
- [ ] All release notes updated
  - release notes are collected in a file named *`Month_Year.md`* in this [repo directory](https://github.com/Microsoft/vscode-docs/blob/vnext/release-notes/)
- [ ] Acknowledge pull requests in release notes. We acknowledge PRs from outside the team. Use the [thankyou](https://github.com/Microsoft/vscode-tools/tree/master/thankyou) utility to generate the initial contents of the section. **owner**
- [ ] Anotable fixes in the release notes **@all**
- When done fixing/verifying and there are changes since last build at the end of day PT
  - [ ] Trigger new insider build and publish it manually **@owner**

##### Friday/Monday
- [ ] Branch code to `release/<x.y> **@zurich**
- [ ] Announce master is open for business **@zurich**
- [ ] Polish release notes **@redmond**

##### Monday/Tuesday
- [ ] Publish `Insider` with hand-picked and reviewed candidate fixes **@owner**

##### Thursday/Friday
- [ ] Merge translations **@zurich**
- [ ] Rebuild for all platforms **@owner**
- [ ] Sanity check of installable bits
  - [ ] Windows
    - [ ] signed installer **@owner**
    - [ ] zip **@owner**
  - [ ] OS X - **@owner**
  - [ ] Linux
    - [ ] deb package 32-bit **@owner**
    - [ ] deb package 64-bit **@owner**
    - [ ] rpm package 64-bit **@owner**
    - [ ] rpm package 32-bit **@owner**
    - [ ] archives **@owner**
- [ ] Publish website **@gregvanl**
- [ ] Publish to stable **@owner**
- [ ] Add a git tag to `HEAD` of `release/<x.y>` in format `x.y.z`
- [ ] Enable scheduled `insider` builds **@owner**
- [ ] Twitter announcement **@seanmcbreen**

### OS Test Availability

| Name          | GitHub Alias   | Linux | Mac | Windows |
| :------------ |:---------------|:-----:|:---:|:-------:|
| Alex          | @alexandrudima |       |     |    x    |
| Andre         | @weinand       |  x    |  x  |    x    |
| Ben           | @bpasero       |  x    |  x  |    x    |
| Brad          | @bgashler1     |  x    |  x  |    x    |
| Chris         | @cdias         |  x    |  x  |    x    |
| Christof      | @chrmarti      |  x    |  x  |    x    |
| Daniel        | @tyriar        |  x    |  x  |    x    |
| Dirk          | @dbaeumer      |       |     |    x    |
| Erich         | @egamma        |       |     |    x    |
| Greg          | @gregvanl      |  x    |  x  |    x    |
| Isidor        | @isidorn       |  x    |  x  |    x    |
| Joao          | @joaomoreno    |  x    |  x  |    x    |
| Johannes      | @jrieken       |  x    |  x  |    x    |
| Kai           | @kieferrm      |  x    |  x  |    x    |
| Martin        | @aeschli       |  x    |  x  |    x    |
| Peng          | @rebornix      |  x    |  x  |    x    |
| Pine          | @octref        |  x    |  x  |    x    |
| Ramya         | @ramya-rao-a   |  x    |  x  |    x    | 
| Rob           | @roblourens    |  x    |  x  |    x    |
| Sandeep       | @sandy081      |  x    |  x  |    x    |
| Sean          | @seanmcbreen   |  x    |  x  |    x    |
| Steven        | @stevencl      |       |     |    x    |
| Wade          | @waderyan      |  x    |  x  |    x    |

### Dev Matrix

|                    |                    |                    |                    |
|:-------------------|:-------------------|:-------------------|:-------------------|
| [ ] @alexandrudima | [ ] @weinand       | [ ] @bpasero       | [ ] @chrmarti      |
| [ ] @tyriar        | [ ] @dbaeumer      | [ ] @egamma        | [ ] @isidorn       |
| [ ] @joaomoreno    | [ ] @jrieken       | [ ] @kieferrm      | [ ] @aeschli       |
| [ ] @rebornix      | [ ] @octref        | [ ] @ramya-rao-a   | [ ] @roblourens    |
| [ ] @sandy081      |                    |                    |                    |