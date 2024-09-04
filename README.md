# sluganator - Software Engineer Exercise

## Overview

You will be building an application that stores URLs and descriptions of various websites. It should also build a url-friendly [slug](https://en.wikipedia.org/wiki/Clean_URL#Slug) from each website's description.

The application should consist of an (HTTP-based) API and a web user interface (ideally a single-page app) that interacts with this API.

Please have a look at [Detailed Requirements](#detailed-requirements) below for a more detailed listing of required functionalities.

### General Guidelines

- Quality matters to us. Take your time and produce a solution you feel comfortable deploying to a production environment.
- Write tests. Unit, integration, acceptance; whatever you are comfortable with and feel is appropriate.
- Please feel free to consult Google if you need to. No one memorizes all the syntax, and we don’t expect you to.
- Make frequent git commits.
- In-memory persistence is fine.

### Technologies

We use the following technologies at Asurint and would prefer solutions built using a similar tech stack:

- Kotlin (or Java)
- Spring Boot
- GraphQL (or REST)
- JPA/Hibernate
- React

That being said, only use the technologies you are already familiar with and in which you will produce the best solution -
a quality solution is more important than the usage of a particular technology.

### How to Submit Your Work

Please push your work into a public personal GitHub repository, e.g., on GitHub, GitLab, or Bitbucket. If possible, provide a link to this repo to us ahead of your interview. If that is not possible, you can share a link with us during the interview process. Please do not submit a PR to this repo directly to maintain confidentiality.

## Detailed Requirements

The application should support:

- registering a website, given its url and description
- generating a url-friendly [slug](https://en.wikipedia.org/wiki/Clean_URL#Slug) from the website's description
- viewing a list of registered websites
- ability to navigate to a "detail" page for each website, where the route for the detail page includes the generated slug

### Website Registration

A website should be able to be "registered" through a form in the UI by supplying a website's URL, description, and, optionally, some additional notes about the website. Using the given description, a "slug" should be generated following the [requirements below](#slug-generation). A confirmation message should be displayed in the UI containing a link to this registered website's [detail page](#detail-page).

For example:  
url: https://www.asurint.com/  
description: "Asurint - Verify Every Hire"  
notes: "I hear that they're hiring!"  
slug: "asurint-verify-every-hire"

### Slug Generation

Please build the following slug generation logic yourself, and do not rely upon any third-party or open-source implementations.

The goal is to convert a website's description into a roughly equivalent URL-friendly string. Invalid special characters should be removed, and words should be separated using a hyphen. Words already separated via a hyphen should remain separated with a hyphen.

The following special characters should not be removed and instead should be replaced with their English representation:

- & -> and
- @ -> at
- % -> percent

All other special/non-alphanumeric characters should be removed.

The output should never result in multiple consecutive hyphen separators or hyphen separators at the beginning or end of the slug.

#### Examples:

| Description                     | Slug                               |
| ------------------------------- | ---------------------------------- |
| Verify Every Hire               | verify-every-hire                  |
| Aunt Millie's & Co., Inc.       | aunt-millies-and-co-inc            |
| Trusted By 99% of Skydivers!    | trusted-by-99-percent-of-skydivers |
| Your local hitch-hiking experts | your-local-hitch-hiking-experts    |

### List Page

Display a list of all registered websites. The list should display each website's original URL, description, and link to its detail page.

### Detail Page

Each registered website should have a "detail" page available, where the route for this page contains the generated slug. The detail page should display a link to the registered website's URL, the description of the website, and any additional notes about that website that were provided. Clicking the link to the website should help you navigate to that website in a new tab.

For example, visiting `/websites/asurint-verify-every-hire` in the UI could render the detail page for https://www.asurint.com/ with the description `Asurint - Verify Every Hire` and the notes `I hear that they're hiring!`.
