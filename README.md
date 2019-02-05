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

