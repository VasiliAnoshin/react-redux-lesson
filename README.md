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
  }
}
</code></pre>
<p>In the line <code>ref={(inputElement) =&gt; this.colorElement = inputElement}</code>, <code>inputElement</code> is a reference to the <code>input</code> DOM element. We are storing a reference to the <code>input</code> DOM element in the <code>colorElement</code> instance property of the <code>Color</code> class.</p>
<p>Please note:</p>
<blockquote>
<p><a target="_blank" href="https://reactjs.org/docs/refs-and-the-dom.html#callback-refs">React will call the ref callback with the DOM element when the component mounts, and call it with <code>null</code> when it unmounts. Refs are guaranteed to be up-to-date before <code>componentDidMount</code> or <code>componentDidUpdate</code> fires.</a></p>
</blockquote>
</div></div>
