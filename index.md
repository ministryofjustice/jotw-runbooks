# Justice On The Web
This site aims to document the team's technical guidance and engineering practices.

## Standards
Borrowing from Google's engineering practices, our aim within JOTW, with respect to our standards, is to always "make sure that the overall code health ...is improving over time ... [and that] all of the tools and processes of code review are designed to this end".

See Google's full [documentation](https://google.github.io/eng-practices/review/reviewer/standard.html) on coding standards.

Monzo also puts forward a number of [principles](https://monzo.com/blog/2018/06/29/engineering-principles) worth consideration.

### Code Review
On this aspect, it seems Google has done an excellent job covering the dos and don'ts. For now we can reference their documentation, however, as a team we can discuss if there are areas in which we diverge from their documentation or are not applicable.

[The Standard of Code Review](https://google.github.io/eng-practices/review/reviewer/standard.html)

TL;DR - see their section on "Principles".

### Style guide
This covers a lot of ground. For now I'm again, going to be referencing Google's documentation as a default where there are gaps but we can continue to update this section where we deviate from Google.

{% assign standards = site.pages
  | where: "standard", true
  | group_by: "category" %}

{% for standard_group in standards %}
{% for standard in standard_group.items %}
* [{{ standard.title }}]({{ standard.url | relative_url }})
{% endfor %}
{% endfor %}

We currently do not have a team style guide for using Git, however, GDS provide a useful default for us to follow:
* [Working with Git](https://gds-way.cloudapps.digital/standards/source-code.html#working-with-git) (External site)

### Testing our applications
Every website, component, or app that we build with a web interface, should be tested against a suite of different browsers and devices. This is to ensure we are meeting a minimum expected standard across government applications and provide a reasonable level of accessibility for all. We currently follow GDS specifications on what browsers to test on,

* [Designing for different browsers and devices](https://www.gov.uk/service-manual/technology/designing-for-different-browsers-and-devices) (External site)
* [Spreadsheet version of GDS list](https://docs.google.com/spreadsheets/d/1zGvXsgNIoMhynFtUV-WS0lqq5QNGY9mIWBzJ3dbIPfI/edit#gid=0) (Google Doc - check it is up-to-date)

While this list meets the minimum requirements, individual sites may have a specific set of requirements based on user testing and research data, that should also be taken into consideration.

#### Assistive technology testing (AT)
We want everyone to be able to access the content within our websites. This means taking into account users who require assistive technologies and understand how they access our web content. This can only be achieved by testing our websites against AT. GDS offer guidance around what ATs we should be using,

* [Testing with assistive technologies](https://www.gov.uk/service-manual/technology/testing-with-assistive-technologies) (External site)

As a team, we are currently working out the best ways to incorporate the above GDS guidance into our testing process.

Interesting further reading on the viewpoint of AT users, can be found at [Responses to the screen reader strategy review](https://heydonworks.com/article/responses-to-the-screen-reader-strategy-survey/) (External site)

## Runbooks

Runbooks have now moved to [Justice On The Web Online Content Flight Rules](https://github.com/ministryofjustice/jotw-online-content-flight-rules) along with details proceedures for empergency situations.

Many runbooks are still currently located in [Confluence](https://dsdmoj.atlassian.net/wiki/spaces/JOWJ/pages/1482326465/WordPress+Sites+Runbook) . TODO: Review and migrate runbooks over those still useful.

## How to guides
{% assign guides = site.pages
  | where: "guide", true
  | group_by: "category" %}

{% for guide_group in guides %}
{% for guide in guide_group.items %}
* [{{ guide.title }}]({{ guide.url | relative_url }})
{% endfor %}
{% endfor %}

## Tools
Devs in the team use a wide selection of tools. Some are critical to the development of our apps and are required. Below are a listing of these critical and the "nice to haves'”.

### Required
* [Git](https://git-scm.com/)
* [Docker](https://www.docker.com/)
* [Composer](https://getcomposer.org/)
* [AWS CLI](https://aws.amazon.com/cli/)
* [WASM](https://github.com/ministryofjustice/wasm)

### Nice to haves
* [TMUX](https://github.com/tmux/tmux/wiki)
* [Term2](https://www.iterm2.com/)

Editors
* [PHPStorm](https://www.jetbrains.com/phpstorm/) (30 Day free trial)
* [VC Code](https://code.visualstudio.com/)

Testing
* [BrowserStack](https://www.browserstack.com/)
* [PHPUNIT](https://phpunit.de/)
* [Behat](https://docs.behat.org/en/latest/)

## Learning
Continuous learning is really important us. To aid in this, we have resources available. Ask around in the team for access, however, some resources may require contacting the service desk for access. Here are some recommended learning resources.

* [Pluralsight](https://www.pluralsight.com/)
* [O'Reilly](https://www.oreilly.com/)
