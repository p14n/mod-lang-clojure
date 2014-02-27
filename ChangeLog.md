# ChangeLog

## [v1.0.0.Beta3](/../../tree/1.0.0.Beta3) - 2014-02-27

Breaking changes:

* The ClojureScript eventbus client now keywordizes map keys when
  deserializing JSON to match the server-side behavior [#106](../../issues/106)

Other Changes:

* `vertx.net/send-file` can now be passed a result handler [#100](../../issues/100)
* You can now pass nREPL middleware to `vertx.repl/start` [#104](../../issues/104)
* A class loader fix that allows you to now deploy clojure modules [#108](../../issues/105)
* `vertx.filesystem.sync/write-file` now properly coerces its data to a Buffer [#109](../../issues/109)

## [v1.0.0.Beta2](/../../tree/1.0.0.Beta2) - 2014-01-30

Changes:

* bound-fn's are now only used for handlers when `vertx.core/*vertx*` is dynamically bound [#96](/../../issues/96)
  Using a bound-fn has a speed penalty, so we now only do it when required.
  **Note:** any user code that was relying on the implicit wrapping of the handler
  fn in a bound-fn may now break.
* Reflection in critical sections removed via type hinting [#67](/../../issues/67)
* Fixed source links to github repo in API docs [#97](/../../issues/97)
* Support added for new offset-based buffer copying in `vertx.buffer/append!` and `vertx.buffer/set!` [#99](/../../issues/99)

## [v1.0.0.Beta1](/../../tree/1.0.0.Beta1) - 2014-01-20

Bug fixes:

* The runtime factory now only shuts down runtimes it creates [#94](/../../issues/94)

New features:

* The `PlatformManager` is now wrapped via the `vertx.embed.platform` ns [#34](/../../issues/34)
* The new chown functionality in 2.1M3 is exposed via `vertx.filesystem/chown` [#93](/../../issues/93)
* The `NetSockets` can now be upgraded to SSL/TLS [#91](/../../issues/91)

## [v0.4.0](/../../tree/0.4.0) - 2013-12-10

Bug fixes:

* `vertx.client.eventbus/on-open` & `vertx.client.eventbus/on-close` now return the eventbus to ease chaining [#81](/../../issues/81)
* nrepl worker threads now have the context for `vertx.core/*vertx*` conveyed [#84](/../../issues/84)
* `vertx.http/listen` now properly honors the port argument in the 2-arity version [#87](/../../issues/87)

New features:

* SockJS authorise and created hooks now supported [#80](/../../issues/80)
* `remote-address` exposed for SockJS sockets, websockets, and net sockets [#79](/../../issues/79)
* The address of a received message is now exposed as `vertx.eventbus/*current-address*` [#77](/../../issues/77)
* `vertx.http/send-file` now supports an optional completion callback [#76](/../../issues/76)
* `vertx.http.sockjs/bridge` now takes an optional bridge-config map [#73](/../../issues/73)

## [v0.3.0](/../../tree/0.3.0) - 2013-11-08

Breaking changes:

* Pass the eventbus to on-open callbacks in the ClojureScript client [#53](/../../issues/53)
* The APIs for the `deploy-*` functions in `vertx.core` have switched to kwarg args [#61](/../../issues/61)
* `vertx.repl/start-repl` and `vertx.repl/stop-repl` have been renamed to `vertx.repl/start` and `vertx.repl/stop` [#62](/../../issues/62)
* The `:stream` key in the response from `vertx.http/upload-file-info` has been renamed `:basis`
* `vertx.http/remote-address` now returns the raw host string as `:host`, instead of the possibly DNS-resolved value [#69](/../../issues/69)
* Exceptions passed to callbacks are now decomposed into maps [#74](/../../issues/74)

Other changes:

* nil message handlers are now properly handled [#56](/../../issues/56)
* Maps were sometimes encoded as JsonArrays [#57](/../../issues/57)
* vertx.logging/get-logger now always returns a logger, even when embedded [#59](/../../issues/59)
* repl/start now properly honors a port argument [#60](/../../issues/60)
* repl/start now writes out the actual bound port to .nrepl-port [#58](/../../issues/58)
* The module can now run under Vert.x 2.1M1 in addition to 2.0.x [#66](/../../issues/66)
* `vertx.http/remote-address` now includes the source InetSocketAddress object as `:basis`
* The module now uses Clojure 1.6.0-alpha2 instead of a custom Clojure build that prevented memory leaks
* (vertx.buffer/append! buf string encoding) now works [#71](/../../issues/71)
* An async DNS client is now provided in `vertx.dns` [#65](/../../issues/65)
* UDP sockets are now supported via `vertx.datagram` [#64](/../../issues/64)
* The new EventBus timeout features from Vert.x core are now supported [#54](/../../issues/54)

## [v0.2.0](/../../tree/0.2.0) - 2013-09-17

* add `with-vertx` convenience macro to embed ns
* Add ClojureScript wrapper around vertxbus.js [#50](/../../issues/50)
* Coerce appropriate sockjs hooks to booleans [#48](/../../issues/48)
* BREAKING CHANGE: Rename event-bus -> eventbus [#49](/../../issues/49)
* Don't require all sockjs hooks to be set [#52](/../../issues/52)

## [v0.1.2](/../../tree/0.1.2) - 2013-08-26
 
* Add additional metadata required by the Vert.x module registry

## [v0.1.1](/../../tree/0.1.1) - 2013-08-26

* Convey bindings for handler functions [#43](/../../issues/43)
* Change the lang-module artifact name (lang-clojure.zip ->
  lang-clojure-mod.zip) to follow Vert.x module registry guidelines

## [v0.1.0](/../../tree/0.1.0) - 2013-08-12 

Initial release
