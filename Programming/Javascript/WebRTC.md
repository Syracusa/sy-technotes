# WebRTC API
+ Reference 
  + https://github.com/webrtc/samples/blob/gh-pages/src/content/peerconnection/pc1/js/main.js

## Open local media
```js
async function start() {
  console.log('Requesting local stream');
  startButton.disabled = true;
  try {
    const stream = await navigator.mediaDevices.getUserMedia({audio: true, video: true});
    console.log('Received local stream');
    localVideo.srcObject = stream;
    localStream = stream;
    callButton.disabled = false;
  } catch (e) {
    alert(`getUserMedia() error: ${e.name}`);
  }
}
```

## Requset Call
```js
async function call() {
  callButton.disabled = true;
  hangupButton.disabled = false;

  console.log('Starting call');
  startTime = window.performance.now();

  const videoTracks = localStream.getVideoTracks();
  const audioTracks = localStream.getAudioTracks();

  if (videoTracks.length > 0) {
    console.log(`Using video device: ${videoTracks[0].label}`);
  }
  if (audioTracks.length > 0) {
    console.log(`Using audio device: ${audioTracks[0].label}`);
  }
  const configuration = {};
  console.log('RTCPeerConnection configuration:', configuration);

  pc1 = new RTCPeerConnection(configuration);
  console.log('Created local peer connection object pc1');
  pc1.addEventListener('icecandidate', e => onIceCandidate(pc1, e));

  pc2 = new RTCPeerConnection(configuration);
  console.log('Created remote peer connection object pc2');

  pc2.addEventListener('icecandidate', e => onIceCandidate(pc2, e));
  pc1.addEventListener('iceconnectionstatechange', e => onIceStateChange(pc1, e));

  pc2.addEventListener('iceconnectionstatechange', e => onIceStateChange(pc2, e));
  pc2.addEventListener('track', gotRemoteStream);

  localStream.getTracks().forEach(track => pc1.addTrack(track, localStream));
  console.log('Added local stream to pc1');

  try {
    console.log('pc1 createOffer start');
    const offer = await pc1.createOffer(offerOptions);
    await onCreateOfferSuccess(offer);
  } catch (e) {
    onCreateSessionDescriptionError(e);
  }
}

```

```js

/* PC1 */
let localStream;
let pc1;

const stream = await navigator.mediaDevices.getUserMedia({audio: true, video: true});
localVideo.srcObject = stream;
localStream = stream;


const videoTracks = localStream.getVideoTracks();
const audioTracks = localStream.getAudioTracks();
if (videoTracks.length > 0) {
    console.log(`Using video device: ${videoTracks[0].label}`);
}
if (audioTracks.length > 0) {
    console.log(`Using audio device: ${audioTracks[0].label}`);
}

pc1 = new RTCPeerConnection({});

localStream.getTracks().forEach(track => pc1.addTrack(track, localStream));

console.log('pc1 createOffer start');
const offer1 = await pc1.createOffer(offerOptions);

console.log(`Offer from pc1\n${offer1.sdp}`);
console.log('pc1 setLocalDescription start');

await pc1.setLocalDescription(offer1);


/* PC2 */
let pc2;

pc2 = new RTCPeerConnection({});

pc2.addEventListener('icecandidate', e => onIceCandidate(pc2, e));
pc2.addEventListener('track', gotRemoteStream);

const offer2 = await pc1.createOffer(offerOptions);
console.log('pc2 setRemoteDescription start');

await pc2.setRemoteDescription(offer2);

const answer = await pc2.createAnswer();
await pc2.setLocalDescription(answer);
await pc2.createAnswer();

await pc2.setLocalDescription(answer);

/* PC1 */
await pc1.setRemoteDescription(desc);

async function onIceCandidate(pc, event) {
    await (getOtherPc(pc).addIceCandidate(event.candidate));
}


/* End */
pc1.close();
pc2.close();

```