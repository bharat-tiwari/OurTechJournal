# throttle vs debounceTime

**throttle** is useful to filter multiple continuously happening event like `mouseDrag` to be captured at regular intervals of e.g. at every 2 seconds instead of continuously emitting the event.

**debounce** is useful when you want to capture the last or ultimate value of a continuously happening event like `mouseDrag` after the user stops `mousedrag` for at least certain amount of time like 2 secs or 500ms.

