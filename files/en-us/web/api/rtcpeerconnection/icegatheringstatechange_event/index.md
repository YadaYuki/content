---
title: 'RTCPeerConnection: icegatheringstatechange event'
slug: Web/API/RTCPeerConnection/icegatheringstatechange_event
tags:
  - API
  - Connection
  - Connectivity
  - Gathering
  - ICE
  - RTCPeerConnection
  - Reference
  - WebRTC
  - WebRTC API
  - events
  - Event
  - icegatheringstatechange
  - state
browser-compat: api.RTCPeerConnection.icegatheringstatechange_event
---
<div>{{APIRef("WebRTC")}}</div>

<p>The <strong><code>icegatheringstatechange</code></strong> event is sent to the {{domxref("RTCPeerConnection.onicegatheringstatechange", "onicegatheringstatechange")}} event handler on an {{domxref("RTCPeerConnection")}} when the state of the {{Glossary("ICE")}} candidate gathering process changes.
  This signifies that the value of the connection's {{domxref("RTCPeerConnection.iceGatheringState", "iceGatheringState")}} property has changed.</p>

<p>When ICE firststarts to gather connection candidates, the value changes from <code>new</code> to <code>gathering</code> to indicate that the process of collecting candidate configurations for the connection has begun. When the value changes to <code>complete</code>, all of the transports that make up the <code>RTCPeerConnection</code> have finished gathering ICE candidates.</p>

<table class="properties">
 <tbody>
  <tr>
   <th scope="row">Bubbles</th>
   <td>No</td>
  </tr>
  <tr>
   <th scope="row">Cancelable</th>
   <td>No</td>
  </tr>
  <tr>
   <th scope="row">Interface</th>
   <td>{{domxref("Event")}}</td>
  </tr>
  <tr>
   <th scope="row">Event handler</th>
   <td>{{domxref("RTCPeerConnection.onicegatheringstatechange", "onicegatheringstatechange")}}</td>
  </tr>
 </tbody>
</table>

<div class="notecard note">
<p><strong>Note:</strong> While you can determine that ICE candidate gathering is complete by watching for <code>icegatheringstatechange</code> events and checking for the value of {{domxref("RTCPeerConnection.iceGatheringState", "iceGatheringState")}} to become <code>complete</code>, you can also have your handler for the {{domxref("RTCPeerConnection.icecandidate_event", "icecandidate")}} event look to see if its {{domxref("RTCPeerConnectionIceEvent.candidate", "candidate")}} property is <code>null</code>. This also indicates that collection of candidates is finished.</p>
</div>

<h2 id="Examples">Examples</h2>

<p>This example creates a handler for <code>icegatheringstatechange</code> events.</p>

<pre class="brush: js">pc.onicegatheringstatechange = ev =&gt; {
  let connection = ev.target;

  switch(connection.iceGatheringState) {
    case "gathering":
      /* collection of candidates has begun */
      break;
    case "complete":
      /* collection of candidates is finished */
      break;
  }
}
</pre>

<p>Likewise, you can use {{domxref("EventTarget.addEventListener", "addEventListener()")}} to add a listener for <code>icegatheringstatechange</code> events:</p>

<pre class="brush: js">pc.addEventListener("icegatheringstatechange", ev =&gt; {
  let connection = ev.target;

  switch(connection.iceGatheringState) {
    case "gathering":
      /* collection of candidates has begun */
      break;
    case "complete":
      /* collection of candidates is finished */
      break;
  }
}, false);</pre>

<h2 id="Specifications">Specifications</h2>

{{Specifications}}

<h2 id="Browser_compatibility">Browser compatibility</h2>

<p>{{Compat}}</p>

<h2 id="See_also">See also</h2>

<ul>
 <li><a href="/en-US/docs/Web/API/WebRTC_API">WebRTC API</a></li>
 <li><a href="/en-US/docs/Web/API/WebRTC_API/Signaling_and_video_calling">Signaling and video calling</a></li>
 <li><a href="/en-US/docs/Web/API/WebRTC_API/Connectivity">WebRTC connectivity</a></li>
 <li><a href="/en-US/docs/Web/API/WebRTC_API/Session_lifetime">Lifetime of a WebRTC session</a></li>
</ul>