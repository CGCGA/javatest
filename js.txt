// ==UserScript==
// @name         新商盟订货
// @namespace    https://github.com/wulnm/
// @version      0.1
// @author       wulnm
// @match        http://sz.xinshangmeng.com/*
// @match        https://sz.xinshangmeng.com/*
// @match        http://sz.jinye.cn/*
// @match        https://sz.jinye.cn/*
// @match        https://cart.taobao.com/*
// @match        https://www.taobao.com/*
// @require      https://cdn.jsdelivr.net/npm/vue/dist/vue.js
// @require      https://cdn.staticfile.org/jquery/3.4.1/jquery.min.js
// @require      https://cdn.bootcss.com/jqueryui/1.12.1/jquery-ui.min.js

// @grant   GM_getValue
// @grant   GM_setValue
// @grant   GM_deleteValue
// @author       You
// @match        http://*/*
// @icon         data:image/gif;base64,R0lGODlhAQABAAAAACH5BAEKAAEALAAAAAABAAEAAAICTAEAOw==
// @run-at document-end
// ==/UserScript==

debugger;
(function() {
    'use strict';

    function sleep(d){
           for(var t = Date.now();Date.now() - t <= d;);
    }

    function newclick(num) {
        setTimeout(function(){

                document.getElementsByClassName("list-item-input-add")[num].click();
        },200*num);

        //setTimeout(function(){
        //    document.getElementsByClassName("xsm-order-list-shuru-input")[num].click();
        //},250*num);

        setTimeout(function(){


            //ev.initEvent("click", true, false);
            //document.getElementsByClassName("cgt-col-qtl-lmt")[num].click();
            //document.getElementsByClassName("adda")[num].dispatchEvent(ev);

            //var temnum = document.getElementsByClassName(list-item-col-right.my-col.my-col-span-7.default)[num].innerText;
            var temnum = document.querySelectorAll('.list-item-col-right.my-col.my-col-span-7.default')[num].textContent.trim();
            console.log(temnum);
            if(temnum < 1) {
                document.getElementsByClassName("list-item-input-del")[num].click();
            } else {
                for(var m1=0; m1<temnum-1; m1++) {
                    document.getElementsByClassName("list-item-input-add")[num].click();
                }
            }


        },300*num);
        //setTimeout(function(){
        //    document.getElementsByClassName("xsm-order-list-shuru-input")[num].click();
        //},350*num);
        //onBlur();
    }

    function addone() {

        var addbuttons = document.getElementsByClassName("list-item-input-add");
        //console.log(addbuttons.length); list-item-input-add
       for(var bt = 0; bt<addbuttons.length; bt++) {
           newclick(bt);
            //setTimeout("console.log("+bt+")", bt*1000);
            //sleep(1000);
            //addbuttons[bt].click();
         //   setTimeout(function(){
                 //addbuttons[bt].click();
           //     console.log(bt);
           // },500*bt);
            //setTimeout(addbuttons[bt].click(), bt*1000);
       }
        //window.location.reload();

        //alert("执行成功");


    }
    function updatenew() {

        var addbuttons = document.getElementsByClassName("adda");
        //console.log(addbuttons.length);
       for(var bt = 0; bt<addbuttons.length; bt++) {
           newup(bt);
       }
    }
    function newup(num) {
        setTimeout(function(){
            for(var m1=0; m1<10; m1++) {
                    document.getElementsByClassName("list-item-input-del")[num].click();
             }
            },200*num);
        //onBlur();
    }
    function cleanall() {
        var addbuttons = document.getElementsByClassName("list-item-input-add");
        //console.log(addbuttons.length); list-item-input-add
       for(var bt = 0; bt<addbuttons.length; bt++) {
           newup(bt);
       }
        //onBlur();
    }

    function addButton() {
        $('body').append('<button id="copyToCS">+1</button>')
        $('#copyToCS').css('width', '200px')
        $('#copyToCS').css('position', 'absolute')
        $('#copyToCS').css('top', '70px')
        $('#copyToCS').css('left', '500px')
        $('#copyToCS').css('background-color', '#28a745')
        $('#copyToCS').css('color', 'white')
        $('#copyToCS').css('font-size', 'large')
        $('#copyToCS').css('z-index', 100)
        $('#copyToCS').css('border-radius', '25px')
        $('#copyToCS').css('text-align', 'center')
        $('#copyToCS').dblclick(function () {
         addone();
        })
        //$('#copyToCS').draggable()

         $('body').append('<button id="copyToCS2">全清0</button>')
        $('#copyToCS2').css('width', '100px')
        $('#copyToCS2').css('position', 'absolute')
        $('#copyToCS2').css('top', '70px')
        $('#copyToCS2').css('left', '750px')
        $('#copyToCS2').css('background-color', '#28a745')
        $('#copyToCS2').css('color', 'white')
        $('#copyToCS2').css('font-size', 'large')
        $('#copyToCS2').css('z-index', 100)
        $('#copyToCS2').css('border-radius', '25px')
        $('#copyToCS2').css('text-align', 'center')
        $('#copyToCS2').dblclick(function () {
         cleanall();
        })
        //$('#copyToCS2').draggable()
    }

    console.log(window.location.href);



        if (
           window.location.href.includes(
               "https://sz.jinye.cn/ebusiness-mall/"
    )
           ) {
            addButton();
        } else if (
           window.location.href.includes(
      "https://cart.taobao.com/cart.htm"
    )
           ) {
            addButton();
        } else if (
            window.location.href.includes(
      "http://sz.jinye.cn/ebusiness-mall/"
    )
           ) {
            addButton();
            }

    // Your code here...
})();
