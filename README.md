# Ionic 4 Lockscreen

Provides a lockscreen UI that has a nice keypad UI.
This is a Ionic 4 application.
Developed for a Point of Sale Application.

## Features

It has a timeout due to inactivity. It has a animated feedback and vibration for touch and wrong password.


## Setup

After cloning or downloading this project.

Install Ionic CLI

```
$ npm install -g ionic
```

Install dependencies

```
$ cd <project>
$ npm install
```


```
$ ionic cordova emulate ios
```

Or, just want to see the keypad UI:

```
$ ionic serve
```

See more at [Get started with Ionic](https://ionicframework.com/getting-started/)

## Lockscreen Module

In this module:

- Component: KeypadPage
- Service: LockscreenService
- sass/modal.scss (for fullscreen modal): needs to be included in global.scss

Dependencies:

- TapticEngine (https://ionicframework.com/docs/native/taptic-engine)
- FingerprintAIO (https://ionicframework.com/docs/native/fingerprint-aio)


### Usage

Include LockscreenModule in src/app/app.module.ts

```
import { LockscreenModule } from './plugins/lockscreen/lockscreen.module';

...
@NgModule({
  imports: [
    BrowserModule,
    IonicModule.forRoot(),
    AppRoutingModule,
    LockscreenModule,
  ],
```

Include LockscreenService in src/app/home/home.page.ts

```
import { LockscreenService } from '../plugins/lockscreen/services/lockscreen.service';

...

  showLockscreen() {
    const options = {
      passcode: CORRECT_PASSCODE,
      enableTouchIdFaceId: this.enableTouchIdFaceId,
    };

    this.lockscreenService.verify(options)
      .then((response: any) => {
        const { data } = response;

        console.info('Response from lockscreen service: ', data);

        if (data.type === 'dismiss') {
          this.isCorrect = data.data;
        } else {
          this.isCorrect = false;
        }
      })
  }
```

## Contact
If you have any questions or any feedback, send me a message: [batusekerci@gmail.com](mailto:batusekerci@gmail.com)


## Credits
Developed upon mrhieu's lockscreen-4 application: https://github.com/mrhieu/lockscreen-4
[https://www.takethatdesign.com](https://www.takethatdesign.com)
