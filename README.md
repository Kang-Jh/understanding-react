# Understanding React for beginners

This project shows how React works for beginners(including myself) with React codes.

This project simplifies React and other related modules which means this does not contain proposal features, development environment codes, etc. Even some APIs are not contained(like createFactory, cloneElement etc.).

It doesn't contain Class Component related modules yet.

**Remember! React is a pure javascript library which means your code runs javascript code not React code**

## Feedback

I'm not a native English speaker and live far from the English. So Grammar and choice of words might be inappropriate. And also I'm new to programming I might have wrong understanding about React. So if you wanna feedback about anything. Please let me know.

## React(./react) Summary

Function Components return or Class Components' render method returns ReactElement that is plain javascript object
(Of course, ReactElement has special property which value is symbol that represents ReactElement).

ReactCurrentOwner and ReactCurrentDispatcher and ReactCurrentBatchConfig are plain object. But their property named "current" will be changed by React Reconciler(./react-reconciler) or ReactDOM(./react-dom).

React Hooks uses ReactCurrentDispatcher (dispatcher will be changed by React Reconciler has methods named as same as React Hooks APIs)

## ReactDOM(./react-dom) Summary

What happen when ReactDOM.render(<App />, container)? Most of the time ReactDOM.render is invoked only once. It is complicated than React package(./react) but simpler than Reconciler.

If ReactDOM.hydrate is used or container is document element or has child, then hydration is going to occur. Don't mind hydration if you're new to React.

React makes container react root following below orders. **FiberRoot is from react-reconciler which is the core of React. So it will be described later.**

1. When ReactDOM.render or ReactDOM.hydrate are invoked, React creates FiberRoot and add it to container's property(named with prefixed string + randomKey, so it is unique) therefore container is marked as root and then listens DOM events.
2. Assign fiberRoot to \_internalRoot property of an object(This object is react root). react root has render method and unmount method. render method takes children as a argument and then update it using reconciler.
3. Assign react root to \_reactRootContainer property to container.
4. Update DOM without batch.

In summary, when ReactDOM.render is invoked, React makes container contains react root in its property and then update DOM.

ReactDOM.render also returns object but most of the time returned object never used so we don't have to care about it.

## React Fiber Reconciler(./react-reconciler) Summary

I clearly failed to understand Reconciler code itself. My ability to understand code of Reconciler is not enough yet. But there are useful documents in official site and externals.

You should read articles and see video on following order.

1. [Reconciliation](https://React.org/docs/reconciliation.html)
2. [React Components, Elements, and Instances](https://reactjs.org/blog/2015/12/18/react-components-elements-and-instances.html)
3. [Building React From Scratch](https://www.youtube.com/watch?v=_MAD4Oly9yg)
4. [Stack Reconciler](https://reactjs.org/docs/implementation-notes.html)
5. [React Fiber Architecture](https://github.com/acdlite/react-fiber-architecture)
6. [Inside Fiber](https://blog.ag-grid.com/inside-fiber-an-in-depth-overview-of-the-new-reconciliation-algorithm-in-react/)

If you want to know how hooks are implemented, reading following articles may help you to understand hooks.

1. [Under the hood of React's hooks](https://medium.com/the-guild/under-the-hood-of-reacts-hooks-system-eb59638c9dba)
2. [Deep dive: How do React hooks really work?](https://www.netlify.com/blog/2019/03/11/deep-dive-how-do-react-hooks-really-work/)

## License of Packages

MIT License

Copyright (c) Facebook, Inc. and its affiliates.

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
