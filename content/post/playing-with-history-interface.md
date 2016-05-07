+++
categories = ["web", "history api"]
date = "2016-04-21T05:22:55+02:00"
description = "My example using History interface"
keywords = ["web", "history", "api"]
title = "Playing with history interface"

+++

I have been playing with [History](https://developer.mozilla.org/en-US/docs/Web/API/History) recently and I commit my sample [here](https://github.com/gmonnerat/history-api-sample).

My goal was seeing how to navigate in the website without reload the page, like with [onhashchange](https://developer.mozilla.org/en-US/docs/Web/API/WindowEventHandlers/onhashchange).

The difference is, the page does not reload when you change the hash. But, with [History](https://developer.mozilla.org/en-US/docs/Web/API/History), I used the [click](https://developer.mozilla.org/en-US/docs/Web/Events/click) event to get the same behaviour.

I still don't know if using [click](ttps://developer.mozilla.org/en-US/docs/Web/Events/click) is good or not. But, until now, is working fine.
