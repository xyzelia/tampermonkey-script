// ==UserScript==
// @name         eh-manage-helper
// @namespace    http://tampermonkey.net/
// @version      2024-01-13
// @description  try to take over the world!
// @author       You
// @match        https://upld.e-hentai.org/managegallery?*
// @match        https://upld.exhentai.org/upld/managegallery?*
// @match        https://upload.e-hentai.org/managegallery?act=new
// @icon         https://www.google.com/s2/favicons?sz=64&domain=e-hentai.org
// @grant        none
// ==/UserScript==
function getyyyymm() {
    var x = new Date();
    var y = x.getFullYear().toString();
    var m = (x.getMonth() + 1).toString();
    var d = x.getDate().toString();
    (d.length == 1) && (d = '0' + d);
    (m.length == 1) && (m = '0' + m);
    const yyyymm = y +'/'+ m;
    return yyyymm;
}

let YYYYMM = getyyyymm();

let config_sea = {suffix_en:"[心海汉化组]",suffix_jp:"[心海汉化组]",folder_select:YYYYMM,
                  ulcomment_content:`翻译:AA 嵌字:BB
心海汉化组首发混沌心海：www.mcseas.club
我们是用爱发电的无偿组
请不要在其他公开平台传播我们翻译的漫画

招募汉化大佬：有兴趣的翻译大佬，有PS基础的修图达人我们都欢迎。群号：1162758695
我们汉化组最近确立的方向，现在会接受混沌心海论坛和汉化组里的汉化愿望
在目前这个阶段，我们会逐步整理和接收大家希望我们汉化的作品
因为本组人员与力量都有限，目前接收的愿望要符合以下条件
1.MC类作品，（因为我们混沌心海是MC类论坛，当然，加了组的大佬们如果真的非常希望汉化某个非MC作品，一样可以）
2.距离发布半年以上

————————————————————————————————————————————————————————`}
let config_person = {suffix_en:"[Chinese]",suffix_jp:"[中国翻訳]",folder_select:"论坛用户投稿",ulcomment_content:"匿名好心人翻译"}
let config = config_sea;

function lookup(id, value)
{
    var ret = undefined;
    if(document.getElementById(id) != undefined)
    {
        var options = document.getElementById(id).childNodes;
        for(let i = 0; i < options.length; i++)
        {
            if(options[i].innerText == value)
            {
                ret = options[i];
                break;
            }
        }
    }

    return ret;
}

function gname_en_modify() {
    const gname_en_input = document.getElementById('gname_en');
    console.log(gname_en_input.value);
    if (!gname_en_input.value.endsWith(config.suffix_en)) {
        console.log("change gname_en")
        gname_en_input.value = gname_en_input.value+" "+config.suffix_en;
    }
    const gname_jp_input = document.getElementById('gname_jp');
    if (!gname_jp_input.value.endsWith(config.suffix_jp)) {
        console.log("change gname_jp")
        gname_jp_input.value = gname_jp_input.value+" "+config.suffix_jp;
    }

    const folderid_element = document.getElementById('folderid');
    let selectedOption = lookup('folderid',config.folder_select);
    if (selectedOption!=undefined) {
        console.log("change folderid",selectedOption.value,selectedOption.innerText);
        folderid_element.value=selectedOption.value;
    }

    const ulcomment_element = document.getElementById('ulcomment');
    console.log(ulcomment_element)
    if (!ulcomment_element.value.startsWith(config.ulcomment_content.slice(0,2))){
        console.log("change ulcomment_element: ", ulcomment_element.value);
        ulcomment_element.value = config.ulcomment_content;
    }

    const langtag_element = document.getElementById('langtag');
    langtag_element.value=3437;
}

(function() {
    'use strict';

    const buttonEle = document.createElement('button');
    buttonEle.id = 'helper-button-01'
    buttonEle.innerText = "start"
    buttonEle.setAttribute("type", "text");
    buttonEle.onclick = function () {gname_en_modify()}
    const uiElement = document.getElementById('ui');
    const formElement = document.getElementById('uploadform');

    uiElement.insertBefore(buttonEle, formElement);
})();
