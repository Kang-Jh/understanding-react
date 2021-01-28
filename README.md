# Understanding React for beginners

This project shows how React works for beginners(including myself) with React codes.

This project simplifies React and other related modules which means this does not contain proposal features, development environment codes, etc.. Even some APIs are not contained(like createFactory, cloneElement etc.).

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

What happen when ReactDOM.render(<App />, container)?

If ReactDOM.hydrate is used or container is document element or has child, then hydration is going to occur. Don't mind hydration if you're new to React.

React makes container react root following below orders.
**Remark: fiberRoot is from react-reconciler which is the core of React. So it will be described later.**

1. When ReactDOM.render or ReactDOM.hydrate are invoked, React creates fiberRoot and add it to container's property(named with prefixed string + randomKey, so it is likely unique) therefore container is marked and then listens DOM events.
2. Assign fiberRoot to \_internalRoot property of an object(This object is react root). react root has render method and unmount method. render method takes children as a argument and then update it using reconciler.
3. Assign react root to \_reactRootContainer property to container.
4. Update DOM without batch.

In summary, when ReactDOM.render is invoked, React make container contains react root in its property and then update DOM first.

ReactDOM.render also returns object but most of the time return object never used, so We don't have to care about it.
