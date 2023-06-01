 - [**ABS
   Extension**](https://drive.google.com/drive/folders/1YJWiM6NSa0GUtap4cTTzVa5bTzh4PiPj)
 -  [**Microsoft
   Rewards**](https://microsoftedge.microsoft.com/addons/detail/microsoft-rewards/bnplfnhcidhhdapmblniehfaaompjlck)
 -  [**AdBlock**](https://microsoftedge.microsoft.com/addons/detail/adblock-%E2%80%94-best-ad-blocker/ndcileolkflehcjpmjnfbnaibdcgglog)
-   [**Tampermonkey**](https://microsoftedge.microsoft.com/addons/detail/tampermonkey/iikmkjmpaadaobahmlepeloendndfphd)

**1. Auto Reload Script**
  

        // ==UserScript==
        // @name        Auto-close tabs
        // @namespace   kandelabr
        // @match       https://*/*
        // @grant       window.close
        // @version     1.1
        // @author      -
        // @description Closes tabs automatically - set waste_of_bits below to hostnames you do not want to visit
        // ==/UserScript==
        
        
        let waste_of_bits = ['bing.com', 'rewards.bing.com']
        
        const sleep = async (milliseconds) => {
            await new Promise(resolve => {
                return setTimeout(resolve, milliseconds)
            });
        };
        
        var re = new RegExp(waste_of_bits.join('|'), "i");
        if (re.test(document.location.host)) {
          await sleep(300000);
          while(true) {
            window.close();
            await sleep(1000)
          }
        }

**2. Microsoft Rewards Bot**

    // ==UserScript==
    // @name         Microsoft Rewards Bot
    // @namespace    http://tampermonkey.net/
    // @version      1.1
    // @description  I will hack microsoft rewards for you!!! You can also do other stuff while it is running.
    // @author       You
    // @match        *://*/*
    // @grant        none
    // ==/UserScript==
    (function() {
    
        'use strict';
        if (document.readyState == "complete" || document.readyState == "loaded" || document.readyState == "interactive") {
            clickCards()
        } else {
    
            document.addEventListener("DOMContentLoaded", function(event) {
                clickCards()
            });
        }
    })();
    
    function clickCards(){
        var first = true
        const params = new URLSearchParams(window.location.search)
        if (params.has('searchTab')){
            if (params.get('first') == "true"){
                localStorage.setItem('numSearch', 0);
            }
            var numSearch = localStorage.getItem('numSearch');
            if (numSearch === null){
                numSearch = 0
            }
            localStorage.setItem('numSearch', parseInt(numSearch) + 1);
            console.log(numSearch)
            if (numSearch >= 90){
                close();
            }
        }
        if (window.location.href === "https://rewards.microsoft.com/"){
            window.open("https://www.bing.com/search?q=abc&searchTab=true&first=true", '_blank').focus();
        }
        if (params.has('rnoreward')){
            setInterval(function(){
                if (document.querySelector(".btOption.b_cards")){
                    document.querySelector(".btOption.b_cards").click()
                }
                if (document.getElementById("rqStartQuiz")){
                    document.getElementById("rqStartQuiz").click()
                }
    
                var largeAnswer = document.querySelectorAll(".b_cards")
                if (largeAnswer.length){
    
                    for (let i = 0; i < largeAnswer.length; i++) {
                        if (largeAnswer[i].getAttribute("iscorrectoption") === "True"){
                            largeAnswer[i].click()
                        }
                    }
                }
    
                var smallAnswer = document.querySelectorAll(".rqOption")
                if (smallAnswer.length) {
                    for (let i = 0; i < smallAnswer.length; i++) {
                        smallAnswer[i].click()
                    }
                }
    
            }, 500)
    
    
        }
        var plus10 = document.querySelectorAll(".mee-icon.mee-icon-AddMedium")
        if (plus10){
          var plus10Length = plus10.length
    
          for (let i = 0; i < plus10Length; i++) {
              console.log(plus10[i])
              plus10[i].parentNode.parentNode.parentNode.parentNode.click()
          }
        }
    
    }

**Extras**
- https://bit.ly/41gxZqB
- [Fitness Video](https://www.reddit.com/r/MicrosoftRewards/comments/11nqkye/new_list_of_ultra_low_time_fitness_points)


**Shopping Trick**

[Shopping from Microsoft Start (msn.com)](https://www.msn.com/en-us/shopping/)

    javascript:var msnShoppingGamePane = document.querySelector("shopping-page-base") ?.shadowRoot.querySelector("shopping-homepage") ?.shadowRoot.querySelector("msft-feed-layout") ?.shadowRoot.querySelector("msn-shopping-game-pane"); msnShoppingGamePane.style.setProperty("grid-area", "slot1"); msnShoppingGamePane.setAttribute('gamestate', 'active'); if(msnShoppingGamePane != null){ msnShoppingGamePane.cardsPerGame = 1; msnShoppingGamePane.resetGame(); }

