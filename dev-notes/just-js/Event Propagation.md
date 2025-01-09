Article: https://dev.to/anshumanmahato/managing-event-flow-a-deep-dive-into-javascript-event-propagation-2gha
## Event Propagation - movement of Events through the DOM

JavaScript uses **Event Propagation** to handle how events travel through the Document Object Model (DOM) when an event occurs and reaches the target element, triggering further actions based on the event.

It happens in three phases - **Capturing**, **Targeting** and **Bubbling**.

**1. Capturing** - This is the first phase in the event propagation process. When an event is triggered, it starts from the root of the DOM tree and then moves down towards the target element. By default, event handlers are not executed in this phase.
**2. Targeting** - This phase starts once the event reaches the element where the event was triggered. Any event handlers associated with the target element for the particular event get executed in this phase.
**3. Bubbling** - After targeting, the event traces back its path and moves back up to the root of the DOM. It is in this phase that the event handlers execute. JavaScript executes the associated event handlers in order as the event moves up the DOM tree.

[[Event Propagation (Schema).canvas|Event Propagation (Schema)]]

## Manipulating Event Propagation

**`event.stopPropagation()`** and **`event.stopImmediatePropagation()`**. Both of them block the propagation of the event once encountered. There is only one difference in their work.

The **`event.stopPropagation()`** stops the event from going to the next element. All handlers associated with the current element for that particular event will still get executed. This does not happen in **`event.stopImmediatePropagation()`** where propagation stops immediately, and no event handlers execute even if they belong to the current element.

## Executing in the Capture Phase

You must have used the **`addEventListener()`** utility with two parameters to attach events to elements - the event type and the handler function. It also takes a third parameter called **`useCapture`**. Its default value is **`false`**. If we pass **`true`** to this, then the handler will be executed at capturing instead of bubbling.
```
element.addEventListener('click',handlerFn,true);
```

## Optimization with Event Delegation

**Event delegation** is a technique where you delegate the event listener to the parent element to listen to events triggered by its children. We usually do this when the children perform similar actions upon an event.
