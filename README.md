# Angular Webcam Video Capture

* Displays webcam video stream and captures images from local PC using a web browser. Photos can be captured using a button that will save the images in an array. Works in Chrome only.

*** Note: to open web links in a new window use: _ctrl+click on link_**

## Table of contents

* [General info](#general-info)
* [Screenshots](#screenshots)
* [Technologies](#technologies)
* [Setup](#setup)
* [Features](#features)
* [Status](#status)
* [Inspiration](#inspiration)
* [Contact](#contact)

## General info

* The captured pictures are added to a 'captures' array. This is cleared each time the app initialises as part of the ngOnInit lifecycle.

* The `srcObject` property of the HTMLMediaElement interface is now used to get webcam video stream due to [deprecation of "createObjectURL"](https://developer.mozilla.org/en-US/docs/Web/API/HTMLMediaElement/srcObject).

## Screenshots

![Example screenshot](./img/webcam-video-capture.png).

## Technologies

* [Angular v7.2.13](https://angular.io/) & [Angular CLI v7.3.8](https://cli.angular.io/).

* [Angular ElementRefs](https://angular.io/api/core/ElementRef#description) used as a wrapper inside of a View. Security issues with this method and it means service workers cannot be used. Better to use templating and databinding or use Renderer2.

* [Angular ViewChild](https://angular.io/api/core/ViewChild) decorator used to configure a view query.

* [navigator.mediaDevices.getUserMediagetUserMedia()](https://developer.mozilla.org/en-US/docs/Web/API/MediaDevices/getUserMedia) method used to prompts the user for permission to use a media input which produces a MediaStream. It returns a Promise that resolves to a MediaStream object. A catch error function was added.

## Setup

Run `ng serve` for a dev server. Navigate to `http://localhost:4200/`. The app will automatically reload if you change any of the source files.

## Code Examples

* Extract from `app.component.ts` showing deprecated `createObjectURL` code and working replacement code.

```typescript

    public ngAfterViewInit() {
        if(navigator.mediaDevices && navigator.mediaDevices.getUserMedia) {
            navigator.mediaDevices.getUserMedia({ video: true }).then(stream => {
                // this.video.nativeElement.src = window.URL.createObjectURL(stream);
                this.video.nativeElement.srcObject = stream;
                this.video.nativeElement.play();
            });
        }
    }


```

## Features

* Works with [Google Chrome Version 73.0.3683.103 Oficial Build 64 bits](https://www.google.com/chrome/).

* Updated to latest Angular 7 version with all dependency conflicts resolved.

## Status & To-Do List

* Status: Simple 100% working app.

* To-Do: add an improved UI. Add database connection to store captured photos.

## Inspiration

* [Nic Raboy of X-Team blog: CAPTURE WEBCAM IMAGES FROM A BROWSER WITH ANGULAR](https://x-team.com/blog/webcam-image-capture-angular/)]

* [Matt McAlister: Get You Some Media With getUserMedia()](https://medium.com/@matt.mcalister93/get-you-some-media-with-getusermedia-726cde161cd7)

## Contact

Created by [ABateman](https://www.andrewbateman.org) - feel free to contact me!
