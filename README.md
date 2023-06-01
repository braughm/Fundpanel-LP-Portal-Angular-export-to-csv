# FundPanel

# Gulp Build Step
1. Update "Environment" ".prod.ts" or "dev.ts" with apiBaseUrl, downloadBaseUrl, loginUrl, returnUrl, logoutUrl with your Org's My Domain URL behind the /xxxx path
2. Update ".env" file with  Username Password and Login URL
3. Pull fresh copy of from Repositor ensure not working dev branch
4. npm run gulp:build:development or npm run gulp:build:production
5. NOTE: Set Environment Variables to Target Org npm run gulp:deploy

This project was generated with [Angular CLI](https://github.com/angular/angular-cli) version 8.3.17.

## Development server

Run `ng serve` for a dev server. Navigate to `http://localhost:4200/`. The app will automatically reload if you change any of the source files.

## Code scaffolding

Run `ng generate component component-name` to generate a new component. You can also use `ng generate directive|pipe|service|class|guard|interface|enum|module`.

## Build

Run `ng build` to build the project. The build artifacts will be stored in the `dist/` directory. Use the `--prod` flag for a production build.

## Running unit tests

Run `ng test` to execute the unit tests via [Karma](https://karma-runner.github.io).

## Running end-to-end tests

Run `ng e2e` to execute the end-to-end tests via [Protractor](http://www.protractortest.org/).

## Further help

To get more help on the Angular CLI use `ng help` or go check out the [Angular CLI README](https://github.com/angular/angular-cli/blob/master/README.md).





FundPanel Change Management Policy
==============


Overview:
--------------
The FundPanel Change Management Policies&#39; purpose is to ensure all code that is published to production is released with controls that help control quality and consistency. This includes ensuring all code is properly unit tested, is peer-reviewed, has been through security and best practice code scanning, when possible, has been through user acceptance testing, and there are options to ensure emergency hotfixes are quick to release yet still conform to our policies.

This policy applies to all Aduro owned or managed code repositories including but not limited to: braughm/Aduro &amp; braughm/fundpanel-portal, braughm/Aduro-ScratchOrgTooling,
 braughm/LP-Portal-Angular.

Types of Code Changes:
--------------
**Major Release** : Major releases are any software update that includes many feature changes, changes that may have significant dependencies or downstream impacts, features that require instructions on how to use, or may significantly impact the workflow of end-users.

- If an update consists of a related group of changes and/or features, then it should be part of a major release.
- If the update has many dependent features and could break many aspects of the application if there was a conflict or bug, then it must be part of a major release.
- If a release requires manual post-deployment steps it must be part of a major release. Major releases must be applied to ALL Org upon releasing the new version.
- Major releases must be communicated to our internal Aduro users, External Users, our Direct Customers. In the case where it impacts the LP Portal, we must also communicate with our customers&#39; customer.

**Minor Release:** Minor release is any software update that consists of 1 feature and has been judged to have minimal risk to the package functionality and minimal dependencies to other features.

- A minor release can NOT potentially break large portions of the package or have many other features dependent on or affected by the release.
- If the release requires post-deployment steps to be manually performed, then it must be included as part of a major release.
- Minor releases must be followed up with communication via Slack to internal Aduro Users on the #FundPanel channel within 2 weeks of release.
- Minor release does not require to be pushed to all Orgs and may only be pushed to Orgs that request the new feature.

**Emergency Hotfix:** An emergency Hotfix is a feature release or bugfix that is prioritized above all other releases.
--------------
- Emergency Hotfixes can be prioritized over other features. 
- A developer can not bypass Unit Testing and must follow our policy for code coverage for any new code. 
- Existing Functional Tests must be run.  
- New Functional Tests must be created within 2 weeks if new functionality is introduced.
- Hotfixes can bypass the requirement for a separate developer to perform the Code Review if committed by the Lead developer or Product Manager only. 
- Document Reason for Bypassing Code Review Step in Github using Github Comment.
- Ensure another Senior Developer performs a Post Code Review within 2 weeks.

**Code Change Process:**
==============


Creating A New Branch
--------------
- For each new feature or bug fix, a new GitHub branch will be created with a name that starts with the Jira Story/Bug/Task Prefix (example: FPLP-234). Any Scratch Orgs or Sandboxes should also include this prefix where possible. New branches must be created from the Development Branch or in the case of Hotfixes the Main production Branch.

Unit Testing
--------------
- All branches must pass basic unit testing with the goal of 100% code coverage, though it is understood in rare situations this is not feasible. A collective of 85% or better code coverage is required on all code before a Pull Request is initiated.

Commits to the Repository
--------------
- Commits should feature one or more Jira Store/Bug/Task prefixes if the Branch addresses multiple cards.
- The Commit should also have a basic description of what is involved in the commit. Often this can simply be the title of the Jira Card.
- The last part of the commit description should indicate anything unique to this commit, such as &quot;Fixed bug found with the previous commit…&quot;. This way when you make multiple commits for the same branch future Developers can understand what the purpose was for each commit if they are searching for a point to roll back.

Pull Request &amp; Peer Review
--------------
- The description on the Pull Request should include the Jira Card prefixes if the Branch addresses multiple cards. The Pull Request should also have a basic definition of what is involved in the commit. Often this can simply be the title of the Jira Card but, if this is part of a follow-up fix to a previous Pull Request, include the unique details to this Pull Request.
- Pull Requests can be initiated by developers but, they must be reviewed and approved by a separate Admin User than the User who initiated the Pull Request.
Exception:The only exception to this is with Emergency Hotfixes the developer can approve their Pull Request if they are an Admin. However, the Pull Request must be reviewed within 2 weeks by a separate user.

Pushing Development Branch into Package
--------------
- Once a Pull Request has been reviewed, approved, and merged into the development branch, the GitHub Admin will deploy a code update to the Package Development Org&#39;s codebase. In the case of the Portal or an update not related to an SFDC Package, the code is deployed to the production server from the Sandbox, Scratch Org, or development environment.

Building New Package &amp; Documenting Changes
--------------
- Once the updated code has been deployed to the SFDC Development Hub sever, then the GitHub Admin will create a new Version for the Package.
- If there are any new components to add they will first add those to the package.
- When Uploading the new package version the version format will be: (MajorVersion#.MinorVersion#) i.e. 9.138. In the Case of a Hotfix, it is treated as Minor Version #.
- For the description of the new version of the Package. The first line must indicate the Release type (Major, Minor, Hotfix). In the next lines copy and paste the same information included in the Pull Request Description. Include any additional information if there are multiple Versions created for a single Pull Request, so descriptions are unique.

Testing &amp; Review Notes Documentation
--------------
- In the Development Hub Org or Production Environment, a Documents folder will be maintained that has a Template document used to track issues with the Package during its finals stages of testing before it is deployed into the production environment. This document will be given the Version Number and Date of the current Release.

Security and Code Review of Managed Package
--------------
- All SFDC Managed Package Code will undergo an annual security scan using: [https://security.secure.force.com/sourcescanner/PackageScannerMain](https://security.secure.force.com/sourcescanner/PackageScannerMain)
- The top section of the results from the scanning report should be copy and pasted in the Testing &amp; Review Notes document. Results of the Scanning will be saved in the Braughm/Aduro repository in the &quot;CodeScanLogs&quot; directory.
- Any Critical issues related directly to the Package Release must be addressed before the Package can be release. Any Critical Issues Not related to the package release must be added to Jira as a Bug and may be considered for a Hotfix if the resolution is urgent, otherwise, they must be fixed on or before the next Major release
- All Critical Issues found in the PackageScanner report will be recorded in the Testing &amp; Review Notes along with the Jira Story/Bug/Hotfix name created to resolve it. If the critical issue is resolved without a Jira card then include details on how it was resolved along with a copy of the results from a second Scan that shows the issue is resolved. Results of the Scanning will be saved in the Braughm/Aduro repository in the &quot;CodeScanLogs&quot; directory.
- If it is determined that the Security and Code Review scan has a false positive for a critical issue please describe in the Testing &amp; Review Notes document how this was determined.

User Acceptance Testing
--------------
- Users Acceptance testing should cover both the happy path and any possible ways the feature can be used by the end-user. The goal is to break things.
- If any significant issues make the feature releases basic requirements unmet or interfere with the normal operation of the application, then it is considered a failure. Upon Failure of UAT it should be explained and documented in the Testing &amp; Review Notes document. Failure of UAT will halt the deployment of the new package version and require it to be fixed and go through the Change Management Process again.
- If the UAT brings up issues but, it is not considered a failure the Release can be deployed but, a new Jira Story/Bug/Task must be created, or a feature request added to the roadmap for future improvement.

Performance Testing
--------------
- Once we have a Performance Testing environment all code must go through basic UAT steps using the large data sets in the performance testing environment. In the meantime, we will leverage our Demo Org along with testing the deployment onto certain Large Production Orgs.
- Any failures must be noted in the Testing &amp; Review Notes document.

Merging Development Branch into the Main Production Branch
--------------
- Once all testing including UAT testing has been completed the Repository Admin will ensure the Development Branch is merged into the Main branch.

Deploying Code to Production
--------------
When Deploying a Release that will be deployed across all Orgs/instances of the application:

- Initially deploy the new version on Demo Orgs and do a quick UAT
- Once deployed on Demo Orgs, deploy it to a small group of Production Orgs that may rarely use the application indicated in our Orgs list.
- Then deploy onto the majority of all Orgs except for our Large High Priority Orgs indicated in our Orgs list.
- Finally, deploy to the group of High Priority Orgs indicated in our Orgs list.
- Document any issue in this version&#39;s Testing &amp; Review Notes document. Create any Jira cards to ensure any conflicts or bugs found are addressed. If minor low priority changes are found add them as an idea to the product roadmap.

User Notification of Code Changes
--------------
- Minor releases must be followed up with communication via Slack to internal Aduro Users on the #FundPanel channel within 2 weeks of release.
- Major releases must be communicated to our internal Aduro users, External Users, our Direct Customers. In the case where it impacts the LP Portal, we must also communicate with our customers&#39; customer.
- Hotfixes do not require communication after deployment, however, if the hotfix is related to a specific Ticket or issue those involved should be notified once it is in production.

--------------
--------------

# export-to-csv | Export to CSV Mini Library
Based off of [this library](https://github.com/javiertelioz/angular2-csv) by Javier Telio

> Helper library to quickly and easily create a CSV file in browser or Node
> 

## Installation

```javascript
yarn add export-to-csv
// npm install --save export-to-csv
```

## Usage
```javascript

import { ExportToCsv } from 'export-to-csv';

var data = [
  {
    name: 'Test 1',
    age: 13,
    average: 8.2,
    approved: true,
    description: "using 'Content here, content here' "
  },
  {
    name: 'Test 2',
    age: 11,
    average: 8.2,
    approved: true,
    description: "using 'Content here, content here' "
  },
  {
    name: 'Test 4',
    age: 10,
    average: 8.2,
    approved: true,
    description: "using 'Content here, content here' "
  },
];

  const options = { 
    fieldSeparator: ',',
    quoteStrings: '"',
    decimalSeparator: '.',
    showLabels: true, 
    showTitle: true,
    title: 'My Awesome CSV',
    useTextFile: false,
    useBom: true,
    useKeysAsHeaders: true,
    // headers: ['Column 1', 'Column 2', etc...] <-- Won't work with useKeysAsHeaders present!
  };

const csvExporter = new ExportToCsv(options);

csvExporter.generateCsv(data);

```

## API


| Option        | Default           | Description  |
| :------------- |:-------------:| -----|
| **fieldSeparator**      | , | Defines the field separator character |
| **filename**      | 'generated' | Sets the name of the downloaded file. ".csv" will be appended to the value provided. |
| **quoteStrings**      | "      | If provided, will use this characters to "escape" fields, otherwise will use double quotes as deafult |
| **decimalSeparator** | .      | Defines the decimal separator character (default is .). If set to "locale", it uses the [language sensitive representation of the number](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number/toLocaleString).|
| **showLabels** | false      | If true, the first row will be the `headers` option or object keys if `useKeysAsHeaders` is present|
| **showTitle** | false      | Includes the title as the first line in the generated file   |
| **title** | 'My Generated Report' | This string will be used as the report title |
| **useBom** | true      | If true, adds a BOM character at the start of the CSV to improve file compatibility |
| **useTextFile** | false      | If true, returns a `.txt` file instead of `.csv` |
| **useKeysAsHeaders** | false      | If true, this will use the keys of the first object in the collection as the column headers|
| **headers** | []      | Expects an array of strings, which if supplied, will be used as the column headers|


# Thanks!

|        Credits and Original Authors        |
| :------------- |
| **[javiertelioz](https://github.com/javiertelioz)** |
| **[sn123](https://github.com/sn123)** |
| **[arf1980](https://github.com/arf1980)** |
