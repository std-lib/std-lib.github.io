# Library Wish List

## Details

 - Libraries marked with a `****` are fully implemented awaiting QA. 
 - Libraries marked with a `***` are mostly implemented.
 - Libraries marked with a `**` are somewhat to partially implemented.
 - Libraries marked with a `*` are researched to barely implemented.

## The List

- `pdo` - Normal PDO but with additional options for large clusters with read/write slaves. (`***`)
- `network` - Wrapper around low-level networking functionality, also wrapping exisitng async implementations. (`**`)
- `std` - Low level functionality for arrays, string, value operations. (`**`)
- `filter` - Wrappers around `filter_*` functionality. (`***`)
- `regex` - Classy/smart wrapper around PRCE regular expressions (`**`)
- `container` - Very thin wrapper around various containers. (`****`)
- `terminal` - VT100, ANSI escape sequence support for terminal (“console”) usage.  No interactivity (prompts), see `binutil`.  Instead, terminal colors, and other low-level escape sequences. (`*`)
- `session` - Various improvements over sessions (multiple backends, layered backends, HTTP PSR support) (`*`)
- `logging` - (?) - `monolog/monolog` wrapper, only integrates into other packages (`*`)
- `process` - Wrapper around `symfony/process` with some improvements / normalization. (`*`)
- `pipeline` - Various “pipeline” or ETL functionality
- `command-bus` - Command bus functionality. (`****`)
- `ssh` - Functionality to connect and interact over SSH. (`**`)
- `notify` - Notification of human beings and escalation.
- `error` / `error-capture` - Simple error handlers; (_todo:_ some overlap with `logging` here); exception-ization of existing PHP-level `E_*` with configurable actions per “type”.  (Example; Undefined variable -> `UndefinedVariableException`, log to PSR-3, or silence, + file/namespace configurability for third party code)
- `redis` - Redis client
- `web-boilerplate` - Simple package providing boilerplate “message” pages; i.e. error pages but not limited to this.

- `daemon` - Wrapper/functionality for `systemd`, `fork()` and other php process control such as pcntl. 
- `binutil` -  “binary utility” functionality; i.e. using scripts interactivly in a VT100 terminal emulator such as xterm (Possibly, merge into `terminal`) 
- `file-config` - Reader for various “config file” formats such as ini, json, toml, yaml, and “``return []``” php files.
- `app-config` - Quick-start functionality using other libraries; facade
- `app-inject`  - (?) Also called `dependency-config`.  Allows intelligent configuration and bootstrapping via `app-config`  + `container`, may be merged with `app-config`. 

- `app` - Boilerplate for any supported framework (Zend 2, Zend 3, Symfony, Laravel) (`****`)
- `app-index` - Boilerplate for web applications (``index.php` front-controller) (`****`)
- `app-terminal` - Interactive terminal boilerplate / bootstrapping (also called: `app-binutil`) (implemented, but need `terminal` to be honestly useful)
- `app-daemon` - Non-interactive long-running daemons, as well as short or long running cron jobs and small tasks.

##### Very Opinionated

These are wrappers around existing frameworks and libraries providing full functionality with less than 100 lines of code.  While not really “a framework” as they are able to be used independently, it is about as far as we go:

- `app-simplweb` - Binds `\Zend\Diactoros`, `\League\Route`, as well as (optionally) `\std\Container` (or any other, optionally with auto-writing dependency injected PDO, Redis, Doctrine, etc) and `\std\Config` (or any other array). (`****`)


