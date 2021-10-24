---
title: browsingData.removeFormData()
slug: Mozilla/Add-ons/WebExtensions/API/browsingData/removeFormData
tags:
  - API
  - Add-ons
  - Extensions
  - Method
  - Reference
  - WebExtensions
  - browsingData
  - removeDownloads
browser-compat: webextensions.api.browsingData.removeFormData
---
<div>{{AddonSidebar()}}</div>

<p>Clears data that the browser has saved for autofilling forms.</p>

<p>You can use the <code>removalOptions</code> parameter, which is a {{WebExtAPIRef("browsingData.RemovalOptions")}} object, to:</p>

<ul>
 <li>clear only form data entered after a given time</li>
 <li>control whether to clear only form data entered in normal web pages or to clear data entered in hosted apps and extensions as well.</li>
</ul>

<p>This is an asynchronous function that returns a <code><a href="/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise">Promise</a></code>.</p>

<h2 id="Syntax">Syntax</h2>

<pre class="brush:js">var removing = browser.browsingData.removeFormData(
  removalOptions            // RemovalOptions object
)
</pre>

<h3 id="Parameters">Parameters</h3>

<dl>
 <dt><code>removalOptions</code></dt>
 <dd><code>object</code>. A {{WebExtAPIRef("browsingData.RemovalOptions")}} object, which may be used to clear only form data entered after a given time, and whether to clear only form data entered in normal web pages or to clear data entered in hosted apps and extensions as well.</dd>
</dl>

<h3 id="Return_value">Return value</h3>

<p>A <code><a href="/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise">Promise</a></code> that will be fulfilled with no arguments when the removal has finished. If any error occurs, the promise will be rejected with an error message.</p>

<h2 id="Browser_compatibility">Browser compatibility</h2>

<p>{{Compat}}</p>

<h2 id="Examples">Examples</h2>

<p>Remove form data saved in the last week:</p>

<pre class="brush: js">function onRemoved() {
  console.log(&quot;removed&quot;);
}

function onError(error) {
  console.error(error);
}

function weekInMilliseconds() {
  return 1000 * 60 * 60 * 24 * 7;
}

var oneWeekAgo = (new Date()).getTime() - weekInMilliseconds();

browser.browsingData.removeFormData(
  {since: oneWeekAgo}).
then(onRemoved, onError);</pre>

<p>Remove all saved form data:</p>

<pre class="brush: js">function onRemoved() {
  console.log(&quot;removed&quot;);
}

function onError(error) {
  console.error(error);
}

browser.browsingData.removeFormData({}).
then(onRemoved, onError);</pre>

<p>{{WebExtExamples}}</p>


<div class="note"><p><strong>Note:</strong> This API is based on Chromium's <a href="https://developer.chrome.com/extensions/browsingData"><code>chrome.browsingData</code></a> API.</p>

<p>Microsoft Edge compatibility data is supplied by Microsoft Corporation and is included here under the Creative Commons Attribution 3.0 United States License.</p>
</div>

<div class="hidden">
<pre>// Copyright 2015 The Chromium Authors. All rights reserved.
//
// Redistribution and use in source and binary forms, with or without
// modification, are permitted provided that the following conditions are
// met:
//
//    * Redistributions of source code must retain the above copyright
// notice, this list of conditions and the following disclaimer.
//    * Redistributions in binary form must reproduce the above
// copyright notice, this list of conditions and the following disclaimer
// in the documentation and/or other materials provided with the
// distribution.
//    * Neither the name of Google Inc. nor the names of its
// contributors may be used to endorse or promote products derived from
// this software without specific prior written permission.
//
// THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS
// "AS IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT
// LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR
// A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT
// OWNER OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL,
// SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT
// LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE,
// DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY
// THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT
// (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE
// OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.
</pre>
</div>