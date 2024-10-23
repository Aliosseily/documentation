---


---

<h2 id="cashout-api-documentation">CashOut API Documentation</h2>
<h3 id="get-apiv1cashoutgetcti">1. <strong>GET /api/v1/cashout/GETCTI</strong></h3>
<ul>
<li>
<p><strong>Description</strong>: Retrieves account information and updates the OTP for the given account.</p>
</li>
<li>
<p><strong>HTTP Method</strong>: <code>GET</code></p>
</li>
<li>
<p><strong>URL</strong>: <code>/api/v1/cashout/GETCTI</code></p>
</li>
<li>
<p><strong>Parameters</strong>:</p>
<ul>
<li><code>accountId</code> (int, required): The unique identifier of the account.</li>
<li><code>otp</code> (int, required): The one-time password (OTP) used to validate the account.</li>
</ul>
</li>
<li>
<p><strong>Response</strong>:</p>
<ul>
<li><strong>Success</strong> (200 OK):
<ul>
<li>Returns the account information along with the updated OTP.</li>
</ul>
</li>
<li><strong>Failure</strong> (404 Not Found):
<ul>
<li>Returns an error message if the account is not found or the OTP is invalid.</li>
</ul>
</li>
<li><strong>Failure</strong> (400 Bad Request):
<ul>
<li>Returns an error message if there is an issue with the request.</li>
</ul>
</li>
</ul>
</li>
<li>
<p><strong>Example Request</strong>:</p>
<p>https</p>
<p><code>GET /api/v1/cashout/getcti?accountId=123&amp;otp=456789</code></p>
</li>
<li>
<p><strong>Example Response (Success)</strong>:</p>
<p>json</p>
</li>
</ul>
<pre class=" language-json"><code class="prism  language-json">    <span class="token punctuation">{</span>
	    <span class="token string">"name"</span><span class="token punctuation">:</span> <span class="token string">"string"</span><span class="token punctuation">,</span>
	    <span class="token string">"otp"</span><span class="token punctuation">:</span> <span class="token number">0</span><span class="token punctuation">,</span>
	    <span class="token string">"amount"</span><span class="token punctuation">:</span> <span class="token number">0</span><span class="token punctuation">,</span>
	    <span class="token string">"currency"</span><span class="token punctuation">:</span> <span class="token number">0</span><span class="token punctuation">,</span>
	    <span class="token string">"currencyName"</span><span class="token punctuation">:</span> <span class="token string">"string"</span><span class="token punctuation">,</span>
	    <span class="token string">"firstName"</span><span class="token punctuation">:</span> <span class="token string">"string"</span><span class="token punctuation">,</span>
	    <span class="token string">"middleName"</span><span class="token punctuation">:</span> <span class="token string">"string"</span><span class="token punctuation">,</span>
	    <span class="token string">"lastName"</span><span class="token punctuation">:</span> <span class="token string">"string"</span><span class="token punctuation">,</span>
	    <span class="token string">"mobileNumber"</span><span class="token punctuation">:</span> <span class="token string">"string"</span>
	<span class="token punctuation">}</span>
</code></pre>
<ul>
<li>
<p><strong>Example Response (Failure - Account Not Found)</strong>:</p>
<p><code>"Account not found! Please check info."</code></p>
</li>
</ul>
<h3 id="post-apiv1cashoutpaycti">2. <strong>POST /api/v1/cashout/PAYCTI</strong></h3>
<ul>
<li>
<p><strong>Description</strong>: Confirms the cashout process for the given account by validating the OTP and other account details.</p>
</li>
<li>
<p><strong>HTTP Method</strong>: <code>POST</code></p>
</li>
<li>
<p><strong>URL</strong>: <code>/api/v1/cashout/PATCTI</code></p>
</li>
<li>
<p><strong>Request Body</strong>:</p>
<ul>
<li><code>CashOutRequest</code> object:
<ul>
<li><code>accountId</code> (int, required): The unique identifier of the account.</li>
<li><code>otp</code> (int, required): The one-time password (OTP) used for verification.</li>
<li><code>amount</code> (long, required): The amount to be cashed out.</li>
<li><code>currency</code> (int, required): The currency of the cashout. [0: LBP, 1: USD]</li>
<li><code>customerName</code> (string, required): The name of the customer.</li>
<li><code>receiptNumber</code> (string, required): The receipt number for the cashout transaction.</li>
</ul>
</li>
</ul>
</li>
<li>
<p><strong>Response</strong>:</p>
<ul>
<li><strong>Success</strong> (200 OK):
<ul>
<li>Returns a success message if the cashout was confirmed.</li>
</ul>
</li>
<li><strong>Failure</strong> (400 Bad Request):
<ul>
<li>Returns an error message if there is an issue with the request.</li>
</ul>
</li>
<li><strong>Failure</strong> (404 Not Found):
<ul>
<li>Returns an error message if the account is not found or the OTP is invalid…</li>
</ul>
</li>
</ul>
</li>
<li>
<p><strong>Example Request</strong>:</p>
<p>https</p>
<p><code>POST /api/v1/cashout/PAYCTI</code><br>
<code>Content-Type: application/json</code></p>
<pre class=" language-json"><code class="prism { language-json"><span class="token punctuation">{</span>
  <span class="token string">"accountId"</span><span class="token punctuation">:</span> <span class="token number">123</span><span class="token punctuation">,</span>
  <span class="token string">"otp"</span><span class="token punctuation">:</span> <span class="token number">456789</span><span class="token punctuation">,</span>
  <span class="token string">"amount"</span><span class="token punctuation">:</span> <span class="token number">500</span><span class="token punctuation">,</span>
  <span class="token string">"currency"</span><span class="token punctuation">:</span> <span class="token number">1</span><span class="token punctuation">,</span>
  <span class="token string">"customerName"</span><span class="token punctuation">:</span> <span class="token string">"John Doe Smith"</span><span class="token punctuation">,</span>
  <span class="token string">"receiptNumber"</span><span class="token punctuation">:</span> <span class="token string">"MJIS20160000004"</span>
<span class="token punctuation">}</span>

</code></pre>
</li>
<li>
<p><strong>Example Response (Success)</strong>:</p>
<p>json</p>
<pre class=" language-json"><code class="prism { language-json"><span class="token punctuation">{</span>
  <span class="token string">"isSuccess"</span><span class="token punctuation">:</span> <span class="token boolean">true</span><span class="token punctuation">,</span>
  <span class="token string">"value"</span><span class="token punctuation">:</span> <span class="token string">"Cashout Success"</span><span class="token punctuation">,</span>
  <span class="token string">"error"</span><span class="token punctuation">:</span> <span class="token keyword">null</span>
<span class="token punctuation">}</span>
</code></pre>
</li>
<li>
<p><strong>Example Response (Failed)</strong>:</p>
<p>json</p>
<pre class=" language-json"><code class="prism { language-json"><span class="token punctuation">{</span>
  <span class="token string">"isSuccess"</span><span class="token punctuation">:</span> <span class="token boolean">false</span><span class="token punctuation">,</span>
  <span class="token string">"value"</span><span class="token punctuation">:</span> <span class="token string">"Cashout Failed"</span><span class="token punctuation">,</span>
  <span class="token string">"error"</span><span class="token punctuation">:</span> <span class="token keyword">null</span>
<span class="token punctuation">}</span>
</code></pre>
</li>
<li>
<p><strong>Example Response (Failure - Account Details Do Not Match)</strong>:</p>
<p>json</p>
</li>
</ul>
<pre class=" language-json"><code class="prism  language-json"><span class="token punctuation">{</span>
  <span class="token string">"isSuccess"</span><span class="token punctuation">:</span> <span class="token boolean">false</span><span class="token punctuation">,</span>
  <span class="token string">"value"</span><span class="token punctuation">:</span> <span class="token keyword">null</span><span class="token punctuation">,</span>
  <span class="token string">"error"</span><span class="token punctuation">:</span> <span class="token string">"Account details do not match! Please check info."</span>
<span class="token punctuation">}</span>
</code></pre>
<ul>
<li>
<p><strong>Example Response (Failure - Account Locked)</strong>:<br>
<code>after 4 failed attempts</code></p>
<p>json</p>
</li>
</ul>
<pre class=" language-json"><code class="prism  language-json"><span class="token punctuation">{</span>
  <span class="token string">"isSuccess"</span><span class="token punctuation">:</span> <span class="token boolean">false</span><span class="token punctuation">,</span>
  <span class="token string">"value"</span><span class="token punctuation">:</span> <span class="token keyword">null</span><span class="token punctuation">,</span>
  <span class="token string">"error"</span><span class="token punctuation">:</span> <span class="token string">"Account is locked due to multiple failed attempts."</span>
<span class="token punctuation">}</span>
</code></pre>
<ul>
<li>
<p><strong>Example Response (Failure - Account Locked)</strong>:<br>
<code>date expires</code></p>
<p>json</p>
</li>
</ul>
<pre class=" language-json"><code class="prism  language-json"><span class="token punctuation">{</span>
  <span class="token string">"isSuccess"</span><span class="token punctuation">:</span> <span class="token boolean">false</span><span class="token punctuation">,</span>
  <span class="token string">"value"</span><span class="token punctuation">:</span> <span class="token keyword">null</span><span class="token punctuation">,</span>
  <span class="token string">"error"</span><span class="token punctuation">:</span> <span class="token string">"Account is locked, please contact support."</span>
<span class="token punctuation">}</span>
</code></pre>

