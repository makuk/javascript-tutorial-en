# 자바스크립트 소개

Let's see what's so special about JavaScript, what we can achieve with it and which other technologies play well with it.

## 자바스크립트가 뭐지?

*자바스크립트* 는 *"웹페이지를 살아있게 하기 위해"* 만들어졌습니다.

이 언어 내에서 프로그램들은 *스크립트*라 불립니다. HTML에 바로 적어서 페이지를 로드할 때 자동적으로 실행되게 할 수 있습니다.

스크립트는 평범한 텍스트로 쓰여져서 실행됩니다. 실행에는 특별한 준비나 컴파일 작업이 필요 없습니다.

이 관점에서 보면, 자바스크립트는 [자바](https://ko.wikipedia.org/wiki/%EC%9E%90%EB%B0%94_(%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%B0%8D_%EC%96%B8%EC%96%B4))라는 언어와는 많이 다릅니다.

```smart header="그럼 왜 <u>자바</u>스크립트죠?"
자바스크립트가 처음 만들어 졌을 땐 이름이 달랐습니다. "LiveScript"였죠. 하지만 그 당시 자바는 매우 유명한 언어였고, 자바와 관련 있는 언어라는 느낌이 드는 것이 유명해지는 데 도움이 될 것 같았기에 자바라는 말을 넣기로 결정되었습니다.

하지만 시간이 지날수록, 자바스크립트는 점점 발전해 완전히 독립된 언어가 되었고, 이제는 .[ECMAScript].(https://ko.wikipedia.org/wiki/ECMA%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8)라는 말로도 불리고 있습니다. 그리고 자바와는 아무런 관계가 아니죠.
```

현재 자바스크립트는 브라우저 내에서만이 아니라 서버에서도, 어떠한 디바이스에서도 [자바스크립트 엔진](https://ko.wikipedia.org/wiki/%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8_%EC%97%94%EC%A7%84)만 있으면 실행이 가능합니다.

브라우저에는 "자바스크립트 가상머신"이라고 불리는 내부 엔진이 있습니다.

엔진이 다르면 그 코드네임도 다릅니다. 예를 들어 보면,

- [V8](https://ko.wikipedia.org/wiki/%ED%81%AC%EB%A1%AC_V8) -- 크롬과 오페라에서 사용됩니다.
- [SpiderMonkey](https://ko.wikipedia.org/wiki/%EC%8A%A4%ED%8C%8C%EC%9D%B4%EB%8D%94%EB%AA%BD%ED%82%A4) -- 파이어폭스에서 사용됩니다.
- ...그 밖에도 IE에서 사용되는 "Trident", "Chakra"나 엣지에서 사용되는 "ChakraCore", 사파리에서 사용되는 "Nitro", "SquirrelFish"가 있습니다.

위에 나온 것들은 기억해 두면 좋은데, 인터넷에서 개발자들의 게시글에서 많이 보이기 때문입니다. 저희도 사용할 거고요. 예를 들어, "X라는 기능이 V8에서 지원됩니다" 라는 것은 크롬과 오페라에서 작동될 것이란 뜻입니다.

```smart header="엔진은 어떻게 작동하나요?"

엔진은 복잡하지만 그 기초는 매우 간단합니다.

1. 엔진 (브라우저라면 그 내부에서) 스크립트를 읽어들입니다(파싱).
2. 그리고 기계어로 스크립트를 번역합니다(컴파일).
3. 그러면 코드가 실행됩니다. 매우 빠르죠.

엔진은 각 단계마다 최적화를 해 줍니다. 게다가 컴파일된 스크립트가 작동될 때도 데이터를 분석하고 기계어 코드에도 최적화를 합니다. 결과적으로 스크립트는 꽤 빨라집니다.
```

## 브라우저 내에서 자바스크립트가 하는 일이 뭐죠?

The modern JavaScript is a "safe" programming language. It does not provide low-level access to memory or CPU, because it was initially created for browsers which do not require it.

The capabilities greatly depend on the environment that runs JavaScript. For instance, [Node.JS](https://wikipedia.org/wiki/Node.js) supports functions that allow JavaScript to read/write arbitrary files, perform network requests etc.

In-browser JavaScript can do everything related to webpage manipulation, interaction with the user and the webserver.

For instance, in-browser JavaScript is able to:

- Add new HTML to the page, change the existing content, modify styles.
- React to user actions, run on mouse clicks, pointer movements, key presses.
- Send requests over the network to remote servers, download and upload files (so-called [AJAX](https://en.wikipedia.org/wiki/Ajax_(programming)) and [COMET](https://en.wikipedia.org/wiki/Comet_(programming)) technologies).
- Get and set cookies, ask questions to the visitor, show messages.
- Remember the data on the client-side ("local storage").

## 브라우저 내의 자바스크립트가 할 수 없는 일은 뭐죠?

JavaScript's abilities in the browser are limited for the sake of the user's safety. The aim is to prevent an evil webpage from accessing private information or harming the user's data.

The examples of such restrictions are:

- JavaScript on a webpage may not read/write arbitrary files on the hard disk, copy them or execute programs. It has no direct access to OS system functions.

    Modern browsers allow it to work with files, but the access is limited and only provided if the user does certain actions, like "dropping" a file into a browser window or selecting it via an `<input>` tag.

    There are ways to interact with camera/microphone and other devices, but they require a user's explicit permission. So a JavaScript-enabled page may not sneakily enable a web-camera, observe the surroundings and send the information to the [NSA](https://en.wikipedia.org/wiki/National_Security_Agency).
- Different tabs/windows generally do not know about each other. Sometimes they do, for example when one window uses JavaScript to open the other one. But even in this case, JavaScript from one page may not access the other if they come from different sites (from a different domain, protocol or port).

    This is called the "Same Origin Policy". To work around that, *both pages* must contain a special JavaScript code that handles data exchange.

    The limitation is again for user's safety. A page from `http://anysite.com` which a user has opened must not be able to access another browser tab with the URL `http://gmail.com` and steal information from there.
- JavaScript can easily communicate over the net to the server where the current page came from. But its ability to receive data from other sites/domains is crippled. Though possible, it requires explicit agreement (expressed in HTTP headers) from the remote side. Once again, that's safety limitations.

![](limitations.png)

Such limits do not exist if JavaScript is used outside of the browser, for example on a server. Modern browsers also allow installing plugin/extensions which may get extended permissions.

## 뭐 때문에 자바 스크립트가 그렇게 특별한 건가요?

There are at least *three* great things about JavaScript:

```compare
+ Full integration with HTML/CSS.
+ Simple things done simply.
+ Supported by all major browsers and enabled by default.
```

Combined, these three things exist only in JavaScript and no other browser technology.

That's what makes JavaScript unique. That's why it's the most widespread tool to create browser interfaces.

While planning to learn a new technology, it's beneficial to check its perspectives. So let's move on to the modern trends that include new languages and browser abilities.


## 자바스크립트 "그 이상"의 언어

The syntax of JavaScript does not suit everyone's needs. Different people want different features.

That's to be expected, because projects and requirements are different for everyone.

So recently a plethora of new languages appeared, which are *transpiled* (converted) to JavaScript before they run in the browser.

Modern tools make the transpilation very fast and transparent, actually allowing developers to code in another language and autoconverting it "under the hood".

Examples of such languages:

- [CoffeeScript](http://coffeescript.org/) is a "syntactic sugar" for JavaScript, it introduces shorter syntax, allowing to write more precise and clear code. Usually Ruby devs like it.
- [TypeScript](http://www.typescriptlang.org/) is concentrated on adding "strict data typing", to simplify development and support of complex systems. It is developed by Microsoft.
- [Dart](https://www.dartlang.org/) is a standalone language that has its own engine that runs in non-browser environments (like mobile apps). It was initially offered by Google as a replacement for JavaScript, but as of now, browsers require it to be transpiled to JavaScript just like the ones above.

There are more. Of course even if we use one of those languages, we should also know JavaScript, to really understand what we're doing.

## 요약
- 자바스크립트는 브라우저 전용 언어로 만들어졌으나, 이제는 다른 곳에서도 많이 쓰이고 있습니다.
- 현재, 자바스크립트는 매우 독특한 위치에 있으며 HTML/CSS와의 완전한 연동을 통해 여러 브라우저에서 다방면으로 쓰이고 있습니다.
- 자바스크립트에서 "유래한" 다른 언어들이 많이 있으며 특정한 기능을 위해 만들어졌습니다. 자바스크립트를 마스터하기 전에 한번쯤은 살펴보는 것을 권장하는 바입니다.
