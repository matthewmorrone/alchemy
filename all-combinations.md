## ![Little Alchemy](http://bit.ly/WSGRxJ "Unlock all combinations in Little Alchemy") Unlock all Combinations in Little Alchemy

### Review

Wanted to finish [Little Alchemy](https://chrome.google.com/webstore/detail/little-alchemy/knkapnclbofjjgicpkfoagdjohlfjhpd?hl=en), but got made fun of for playing it - so I found a loophole. Thanks to [@meatbody](http://twitter.com/meatbody) for trolling me into doing this.

### Instructions

 1. Go to and Play [Little Alchemy](http://littlealchemy.com/).
 1. Open your JavaScript console (`Command + j` or `View >> Developer >> JavaScript Console`)
 1. Copy paste the JavaScript below into the JavaScript console then hit `ENTER`
 1. Refresh the page to see all the unlocked combinations in the side panel 
 2. If you run this script and already have a lot of combinations figured out it may run pretty slowly (not sure why, probably the `$` name-attribute lookup)...
 
#### (3) Copy + Paste this into the `console`

```javascript
(function cheat(combinations){var results=[],matches=[],total=5;buildMatchList();saveMatchList();console.log("--------------------------------");console.log("::work complete:: now refresh.");console.log("--------------------------------");function saveMatchList(){alchemy.history.parents=[];matches.map(function(r){alchemy.history.parents.push(r)});alchemy.saveProgress(true)}function buildMatchList(){var match,i,ii,iii,pos;for(i=0;i<combinations;i++){results[i]=alchemy.potentialOffspring(i)}for(i=0;i<results.length;i++){for(ii=0;ii<results[i].length;ii++){match=results[i][ii];if(!matches[match]){for(iii=0;iii<results.length;iii++){pos=results[iii].indexOf(match);if(pos>-1){if(isMatch([i,iii],match)){break}else if(isMatch([iii,iii],match)){break}}}if(!matches[match]){if(!isMatch([i,i],match)){console.log("!!!!!",match,getAlchemyName(match),i,getAlchemyName(i))}}}}}}function isMatch(m,match){var combo=alchemy.sex(m),pos=combo.indexOf(match)>-1,len=combo.length;if(len&&pos){matches[match]=m;console.log(total+":"+getAlchemyName(match)+" = "+getAlchemyName(m[0])+" + "+getAlchemyName(m[1]));total++;return true}return false}function getAlchemyName(id){return $(alchemy.originStr(id)).filter("h2").find("img").attr("alt")}})(450);
```
### Screenshot of What Happens

![What you should see after running the script](http://f.cl.ly/items/441B2l1S0Y3k383a1X2R/Screen%20Shot%202013-02-11%20at%2012.39.41%20AM.png)
----

### Unminified JavaScript 

The unminified script is included below for your review.
