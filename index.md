# Justice On The Web
This site aims to document the team's technical guidance and engineering practices.

## Standards
Borrowing from Google's engineering practices, our aim within JOTW, with respect to our standards, is to always "make sure that the overall code health ...is improving over time ... [and that] all of the tools and processes of code review are designed to this end".

See Google's full [documentation](https://google.github.io/eng-practices/review/reviewer/standard.html) on coding standards.

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

## Runbooks
Runbooks are currently located in [Confluence](https://dsdmoj.atlassian.net/wiki/spaces/JOWJ/pages/1482326465/WordPress+Sites+Runbook)

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
