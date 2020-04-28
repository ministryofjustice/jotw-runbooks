# Justice On The Web
This site aims to document the team's technical guidance and engineering practices.

## Standards
Borrowing from Google's engineering practices, our aim within JOTW, with respect to our standards, is to always "make sure that the overall code health ...is improving over time ... [and that] all of the tools and processes of code review are designed to this end".

See Google's full [documentation](https://google.github.io/eng-practices/review/reviewer/standard.html) on coding standards.

### Languages
On the PHP front, this is still open to discussion but we are aiming to follow the [PSR standards](https://www.php-fig.org/psr/). Preferably, PSR12 for all PHP code, either in a theme, plugin or microservice.
* [PHP12](https://www.php-fig.org/psr/psr-12/)

Start formatting and linting your code to this standard one option is to use [PHP_CodeSniffer](https://github.com/squizlabs/PHP_CodeSniffer) however, there may also be plugins for your specific code editor.

### Code Review
On this aspect, it seems Google has done an excellent job covering the dos and don'ts. For now we can reference their documentation, however, as a team we can discuss if there are areas in which we diverge from their documentation or are not applicable.

[The Standard of Code Review](https://google.github.io/eng-practices/review/reviewer/standard.html)

TL;DR - see their section on "Principles".

### Style guide
This covers a lot of ground. For now I'm again, referencing Google's documentation where applicable but we will have to revisit this area.

* [HTML/CSS Guide](https://google.github.io/styleguide/htmlcssguide.html)
* [Javascript?](https://google.github.io/styleguide/jsguide.html)

There is also the [JS standard](https://standardjs.com/) which we may want to follow. We'll have to have further discussions as a team on the standards around JS.

* [Working with Git](https://gds-way.cloudapps.digital/standards/source-code.html#working-with-git)

## Runbooks
Runbooks are currently located in [Confluence](https://dsdmoj.atlassian.net/wiki/spaces/JOWJ/pages/1482326465/WordPress+Sites+Runbook)

## Guides

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
