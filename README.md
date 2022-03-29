# Map
Augmented reality is getting more prevalent and easier to use. (AR.js)[https://ar-js-org.github.io/AR.js-Docs/] is a web library to use AR right in your mobile browser. In theory, it's really great! But in practice, it's going to be really difficult to make work on any guest's phone.

The library is good for markers (like QR codes or alternatives) and image tracking.

The library is built on top of an AR/VR framework called Aframe. If you want to customize an experience from the code examples, you'll need to know the different elements in this library.

Though it would be nice to use p5 with this, I'm not sure it's possible currently due to integration and security issues. For now, we're going to be using plain old HTML and JS.

We're going to need to access the Github pages I've created on our phones, and learning from this tutorial, I've generated a QR code for this URL for your phones. How meta!

QR code for this page

Marker
I have adapted the example for using a marker and it's viewable here

The code is here.

Assuming you can load the page on your phone, just scan this Hiro image and it should overlay a 3D model.

Hiro image

The advantage of this library is we can use AR over semi-boring real life triggers, rather than just link to a URL.

Instead of a 3D model, we can add shapes, but replacing the 'entity' with this code:

<a-entity geometry="primitive: sphere; radius: 1.5"
  light="type: ambient; color: white;"
  material="color: white;"
  position="0 0 0"
  scale="0.25 0.25 0.25"
  >
</a-entity>
Image Tracking
The most fun option (but most difficult) is using custom images as markers.

Here is a customized example of the one on the documentation page that should use this image as a marker:

pinball

The code is here.

Big problem: It is super memory intensive, and as I tried to customize this, I kept getting memory errors.

Overly
As I was searching for easier ways to integrate image tracking, I found this app. It's really simple to use, and no code. Problem: In the free version, you can only overlay a video over an image. It's still a pretty seamless interaction, except you'd need to have guests use the Overly app.

NFC
NFC (Near Field Communiction) is built on RFID technology. It's the technology we use when we pay for something with our phone, bank cards, etc.

There is new experimental Google Chrome technology to let your phone read NFC tags. The stipulations:

Newer Android phone
Only through Chrome
Unfortunately, I don't have working devices to test it. But if someone does, they can see if it works here: https://googlechrome.github.io/samples/web-nfc/

Usually our phones work the other way, utilizing a 'tag' in the phone itself, and using readers. This approach wouldn't work for our experiences though, without some heavy engineering. The order would have to go something like:

Guest launches website for your project
Scans RFID scanner, connected to Arduino, connected to the web
RFID scanner communicates to a server
Server communicates to the website that the guest is on, and triggers something to happen
This would take a long time to demo, so this will be a specialty case.
