## AdMob Plugin IO

Cordova / PhoneGap Plugin for Google Ads, including AdMob / DFP (doubleclick for publisher) and mediations to other Ad networks.

## Description

This Cordova / PhoneGap plugin enables displaying mobile Ads with single line of javascript code. Designed for the use in HTML5-based cross-platform hybrid games and other applications.

Ad Types:
- [x] Banner
- [x] Interstitial (text, picture, video)
- [x] Reward Video



## Installation
    ionic cordova plugin add cordova-plugin-admobio


## Usage

Show Mobile Ad with single line of javascript code.

Step 1: Create Ad Unit Id for your banner and interstitial, in [AdMob portal](http://www.admob.com/), then write it in your javascript code.

```javascript
// select the right Ad Id according to platform
  var admobid = {};
  if( /(android)/i.test(navigator.userAgent) ) { // for android & amazon-fireos
    admobid = {
      banner: 'ca-app-pub-xxx/xxx', // or DFP format "/6253334/dfp_example_ad"
      interstitial: 'ca-app-pub-xxx/yyy'
    };
  } else if(/(ipod|iphone|ipad)/i.test(navigator.userAgent)) { // for ios
    admobid = {
      banner: 'ca-app-pub-xxx/zzz', // or DFP format "/6253334/dfp_example_ad"
      interstitial: 'ca-app-pub-xxx/kkk'
    };
  } else { // for windows phone
    admobid = {
      banner: 'ca-app-pub-xxx/zzz', // or DFP format "/6253334/dfp_example_ad"
      interstitial: 'ca-app-pub-xxx/kkk'
    };
  }
```

Step 2: Want cheap and basic banner? single line of javascript code.

```javascript
// it will display smart banner at top center, using the default options
if(AdMob) AdMob.createBanner({
  adId: admobid.banner,
  position: AdMob.AD_POSITION.TOP_CENTER,
  autoShow: true });
```

Step 3: Want interstitial Ad to earn more money ? Easy, 2 lines of code. 

```javascript
// preppare and load ad resource in background, e.g. at begining of game level
if(AdMob) AdMob.prepareInterstitial( {adId:admobid.interstitial, autoShow:false} );

// show the interstitial later, e.g. at end of game level
if(AdMob) AdMob.showInterstitial();
```

Or, you can just copy this [admob_simple.js](https://github.com/floatinghotpot/cordova-admob-io/blob/master/test/admob_simple.js) to your project, change the ad unit id to your own, and simply reference it in your index.html, like this:
```html
<script type="text/javascript" src="admob_simple.js"></script>
```

Remember to remove `isTesting:true` if release for production.



## API

Methods:
```javascript
// use banner
createBanner(adId/options, success, fail);
removeBanner();
showBanner(position);
showBannerAtXY(x, y);
hideBanner();

// use interstitial
prepareInterstitial(adId/options, success, fail);
showInterstitial();
isInterstitialReady(function(ready){ if(ready){ } });

// use reward video
prepareRewardVideoAd(adId/options, success, fail);
showRewardVideoAd();

// set values for configuration and targeting
setOptions(options, success, fail);

// get user ad settings
getAdSettings(function(inf){ inf.adId; inf.adTrackingEnabled; }, fail);
```

Events:
```javascript
// onAdLoaded
// onAdFailLoad
// onAdPresent
// onAdDismiss
// onAdLeaveApp
document.addEventListener('onAdFailLoad', function(e){
    // handle the event
});
```

## Credits

This project is created and maintained by Raymond Xie.

More Cordova/PhoneGap plugins by Raymond Xie, [find them in plugin registry](http://plugins.cordova.io/#/search?search=rjfun), or [find them in npm](https://www.npmjs.com/~floatinghotpot).

Project outsourcing and consulting service is also available. Please [contact us](mailto:rjfun.mobile@gmail.com) if you have the business needs.


