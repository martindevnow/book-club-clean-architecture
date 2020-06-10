# Chapter 31: The Web is a Detail

From an architectural perspective, the adoption of the Web, shouldn't have changed anything. The author details how the computing has occilated between server and client over the years, from server farms, to browser applets, back to servers, then to JS in browser, then moving the JS back to servers in Node.

## The Endless Pendulum

The web didn't start this trend of moving where the computer power lies, either centralized or distributed. But as architects, we must consider the long-term.

The author discusses two examples where on the whim of the marketing team, a financial application and smart phone operating system dramatically changed their UI with the current trends. He only hopes the UI was decoupled from the UI to insulate the developers from most of the impact this change could have.

## The Upshot

The WEB is an IO device. The GUI is a detail that should be "hidden" behind boundaries that keep them separate from the core business logic.

Some argue that a GUI is so unique and rich that it is impractical to pursue device-independent architecture. While this is true to an extent, another boundary between the UI and application _can_ be abstracted.

At some point in the dance between the GUI and the application, the input data can be said to be "complete", allowing the use-case to be executed. Upon completion, the resultant data can be fed back into the dance between the UI and the application. With this approach, we can consider each use case to be operating the IO device of the UI in a device-independent manner.

## Conclusion

> This kind of abstraction is not easy, and it will likely take several iterations to get just right. But it is possible. And since the world is full of marketing geniuses, it’s not hard to make the case that it’s often very necessary.
