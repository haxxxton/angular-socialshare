Angular Social Share
=========

Angular Social Share is a collection of directives which lets you easily share your links various social networks. Currently Facebok, Google, Twitter and Linkdin are supported. Social Networks get the Meta data of the shared content like Title, Summary and Image from the Meta tags on the page by scraping. But Single Page Apps like Angular are unable to support crawling. But these dirictives use alternative so that Meta data is displayed where it is possible. 
Checkout the [Demo].
Getting Started
-----
Install the library through bower.
```js
bower install angular-socialshare.
```
Include the script (and optional css file) in your html file.
```html
<style rel='stylesheet' type='text/css' href="bower_components/angular-socialshare/angular-socialshare.min.css"></style>
<script src="bower_components/angular-socialshare/angular-socialshare.min.js"></script>
```

Add to your APP's dependency.
```js
angular.module('testing',['djds4rce.angular-socialshare'])
```
IMPORTANT
----
For Correct Sharing of links and updating share count you must enable HTML5 Mode True for your application. i.e No `#` in URL'S .
```js
angular.module('testing').config(function($locationProvider){
    $locationProvider.html5Mode(true).hashPrefix('!');
});
```
HTML5 Mode requires server configration [Explained Here] 


Share on Facebook
----
Facebook share uses facebook API which requires us to provide a APPID. Register a facebook app and Configure the APPID in your appplication. Note that you will get an error regarding 'not permitted URL' if you are testing this button in a localhost environment.

```js
angular.module('testing').run(function($FB){
  $FB.init('YOUR_APPID');
});
```
Use the Facebook Directive
```html
 <a facebook class="facebookShare" data-url='http://google.com' data-shares='shares'>{{ shares }}</a>
```
As we are using Facebook share API and not the facebook share button, you will have to style your own Facebook button, or use the provided stylesheet that has styles for the horizontal count button. You also need to display the share count, which the directive fetches from a diffrent API. The directive has transclusion set to true. The latest Facebook share API only allows for a URL to be supplied, it will scrape the other data (image, title, description) from the supplied URL.

The Attributes for the directives are
```js
/*
data-url: URL of the Shared Content
data-shares: The Scope variable on which share count will be binded to. This lets you put
multiple share buttons on a single page and bind the share count to the respective model object.
*/
```

Twitter
----
Include the twitter javascript in your HTML. 
```html
<script src="http://platform.twitter.com/widgets.js"></script>
```
Add Directive to the element where you want to display your Twitter Button
```html
<a twitter  data-lang="en" data-count='horizontal' data-url='http://google.com' data-via='notsosleepy' data-size="medium" data-text='Testing Twitter Share' ></a>
```
The Attributes for the directives are
```js
/*
data-lang: Language of the tweet
data-url: URL of the Shared Content
data-count: Position of the share counter
data-size: Size of the tweet button
data-text: Content of the tweet
data-via: User handle which will be tagged in the tweet
For options checkout https://dev.twitter.com/docs/tweet-button
*/
```
Linkedin
----
Although Linkedin has a share button and also a Javascript share API it does not take the title and the content as its parameters hence we will have to use the raw share URL to share the content.

Use the Linkedin Directive
```html
<div linkdin class="linkedinShare" data-url='http://www.google.com.au' data-title='Linkedin Share' data-summary="testing Linkedin Share" data-shares='linkedinshares'>{{linkedinshares}}</div>
```
Linkedin Directive works similar to the Facebook Mechanism. This will force us to add our own style to the button and also display count which is fetched by the directive through a diffrent API. The supplied stylesheet contains styling for the horizontal styled button.

The Attributes for the directives are
```js
/*
data-title: Title of the Shared Content
data-url: URL of the Shared Content
data-summary: Summary of the content
data-shares: The Scope variable on which share count will be binded to. This lets you put
multiple share buttons on a single page and bind the share count to the respective model object.
*/
```

Google +
----
```html
 <div gplus class="g-plus" data-size="tall" data-annotation="bubble" data-href='http://google.com' data-action='share'></div>
```
For more information on the share button attributes check the [Google Share Documentation]
>If you change the class of the button to `g-plusone' it will be converted to a google plus one button.


**Made with Love by [Djds4rce]**
**Additions with ♡ by [haxxxton]**



[Explained Here]:http://ericduran.io/2013/05/31/angular-html5Mode-with-yeoman/
[Demo]:http://plnkr.co/edit/zO5ujLhFP3yT4eKJcAmz?p=preview    
[Google Share Documentation]:https://developers.google.com/+/web/share/
[Djds4rce]:http://djds4rce.wordpress.com/
[haxxxton]:http://gaandder.com/
