In this lesson, we're going to move away from our application being plain HTML and convert it to being powered by React. To do that, we'll need to add a number of libraries:
<p>Here are the packages that we'll be adding to the project</p>
<pre><code class="lang-html"><span class="hljs-tag">&lt;<span class="hljs-title">script</span> <span class="hljs-attribute">src</span>=<span class="hljs-value">"https://unpkg.com/react@16.3.0-alpha.1/umd/react.development.js"</span>&gt;</span><span class="undefined"></span><span class="hljs-tag">&lt;/<span class="hljs-title">script</span>&gt;</span>
<span class="hljs-tag">&lt;<span class="hljs-title">script</span> <span class="hljs-attribute">src</span>=<span class="hljs-value">"https://unpkg.com/react-dom@16.3.0-alpha.1/umd/react-dom.development.js"</span>&gt;</span><span class="undefined"></span><span class="hljs-tag">&lt;/<span class="hljs-title">script</span>&gt;</span>
<span class="hljs-tag">&lt;<span class="hljs-title">script</span> <span class="hljs-attribute">src</span>=<span class="hljs-value">"https://unpkg.com/babel-standalone@6.15.0/babel.min.js"</span>&gt;</span><span class="undefined"></span><span class="hljs-tag">&lt;/<span class="hljs-title">script</span>&gt;</span>
</code></pre>

<code>ref</code>
<blockquote>
<p><a target="_blank" href="https://reactjs.org/docs/refs-and-the-dom.html#callback-refs">Refs provide a way to access DOM nodes or React elements created in the render method.</a></p>
</blockquote>

<h2 id="when-to-use-refs">When to Use Refs</h2>
<blockquote>
<ul>
<li>Managing focus, text selection, or media playback.</li>
<li>Triggering imperative animations.</li>
<li>Integrating with third-party DOM libraries.</li>
</ul>
</blockquote>

<div class="ltr"><div class="index-module--markdown--2MdcR ureact-markdown "><p>Let's take a look at a similar example:</p>
<pre><code class="lang-js"><span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">Color</span> <span class="hljs-keyword">extends</span> <span class="hljs-title">React</span>.<span class="hljs-title">Component</span> </span>{
  alertTextInput = e =&gt; {
    e.preventDefault();
    alert(<span class="hljs-keyword">this</span>.colorElement.value);
  };
  render() {
    <span class="hljs-keyword">return</span> (
      <span class="xml"><span class="hljs-tag">&lt;<span class="hljs-title">div</span>&gt;</span>
        <span class="hljs-tag">&lt;<span class="hljs-title">input</span>
          <span class="hljs-attribute">type</span>=<span class="hljs-value">"text"</span>
          <span class="hljs-attribute">placeholder</span>=<span class="hljs-value">"Add Input"</span>
          <span class="hljs-attribute">ref</span>=<span class="hljs-value">{(inputElement)</span> =&gt;</span> 
           this.colorElement = inputElement}
        /&gt; 
  )}
}
</code></pre>
<p>In the line <code>ref={(inputElement) =&gt; this.colorElement = inputElement}</code>, <code>inputElement</code> is a reference to the <code>input</code> DOM element. We are storing a reference to the <code>input</code> DOM element in the <code>colorElement</code> instance property of the <code>Color</code> class.</p>
<p>Please note:</p>
<blockquote>
<p><a target="_blank" href="https://reactjs.org/docs/refs-and-the-dom.html#callback-refs">React will call the ref callback with the DOM element when the component mounts, and call it with <code>null</code> when it unmounts. Refs are guaranteed to be up-to-date before <code>componentDidMount</code> or <code>componentDidUpdate</code> fires.</a></p>
</blockquote>
</div></div>

<h4 id="componentdidmount-"><code>componentDidMount()</code></h4>
<blockquote>
<p><a target="_blank" href="https://reactjs.org/docs/react-component.html#componentdidmount"><code>componentDidMount()</code> is invoked immediately after a component is mounted (inserted into the tree)...If you need to load data from a remote endpoint, this is a good place to instantiate the network request.</a></p>
</blockquote>

<h4 id="forceupdate-"><code>forceUpdate()</code></h4>
<blockquote>
<p><a target="_blank" href="https://reactjs.org/docs/react-component.html#forceupdate">By default, when your component’s state or props change, your component will re-render. If your <code>render()</code> method depends on some other data, you can tell React that the component needs re-rendering by calling <code>forceUpdate()</code>.</a></p>
</blockquote>

<blockquote>
<p><a target="_blank" href="https://reactjs.org/docs/react-component.html#forceupdate">Calling <code>forceUpdate()</code> will cause <code>render()</code> to be called on the component, skipping <code>shouldComponentUpdate()</code>. This will trigger the normal lifecycle methods for child components, including the <code>shouldComponentUpdate()</code> method of each child. React will still only update the DOM if the markup changes.</a></p>
</blockquote>

<div class="ltr"><div class="index-module--markdown--2MdcR ureact-markdown "><h4 id="lesson-challenge">Lesson Challenge</h4>
<p>Read these articles: <a target="_blank" href="https://medium.com/netscape/component-state-vs-redux-store-1eb0c929277">Component State vs Redux Store</a> and <a target="_blank" href="https://medium.com/prod-io/react-redux-architecture-part-1-separation-of-concerns-812da3b08b46">React + Redux Architecture : Separation of Concerns</a>. Answer the following questions : </p>
<p>1) Explain how React interplays with Redux.</p>
-If a component holds state and manipulates it, it’s a smart component and if a component just displays data which it receives in the form of props, then it get’s classified as a presentational component.
-When ever state needs to be shared by multiple components or multiple pages and we need to persist some data over route changes, all that data should go inside the redux store.
 let’s say all those products have a buy now button and we have a cart which should keep all those items for which the buy now button has been clicked.This cart information needs to be persisted on a lot of pages and across components like the header component where in we will show the cart count, the checkout page and the payment page.This is a clear indication that the products added in the cart should go inside the redux store rather than the component state.This brings us to another distinction between components:-
Any component which is connected with the redux store is classified as a Container component.It can dispatch actions and update the redux store via the reducers.The components which aren’t connected to the redux store go inside the components folder.Now these components can also further be classified as Smart and Dumb because even though they are not connected to the redux store, they still can hold state by calling some API and persisting that data only till the lifetime of that component.  
<p>2) Give an example that illustrates the Separation of Concerns Principle. </p>
Separation of concerns (SoC) is a design principle for separating a computer program into distinct sections. Each section addresses a separate concern.
<h5>1) React/Representation part</h5>
What it should do
Render HTML content with the data provided.
Have multiple UI states depending on the data, so that you understand why it is shown.
Dispatch actions on user interaction or life cycle events (conditional)
Animation using ReactCSSTransitionGroup or any other libraries.
What it shouldn’t do
React is a representation library. It should give a view of the data provided to it and nothing more than that.
<h5>2)Redux part</h5>
  It has 3 parts: Actions, Reducers, and Store. I have put the concerns into 2 groups:

Brain — This will use only the Actions part of Redux
Storage — This will use Reducers and Store
1. Brain
So, the application data is maintained in redux store and representation in React. Everything else which will be a part of your application will come in the “brain”. It will decide how your application functions and what representation to be shown.
2. Storage
This will contain reducers (pure functions) and a single object called store which will save your application state
The only way to change its state is by dispatching an action. It’ll update depending upon the action type and the data passed with the action
The Store will trigger events when its state is updated.
The view can subscribe to those events and update itself accordingly.

  
</div></div>


