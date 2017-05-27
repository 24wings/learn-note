
```javascript
import fs = require('fs');
import path = require('path');
import cheerio = require('cheerio');
var allFiles = [];
function scannerFileList(dir) {

    var files = fs.readdirSync(dir);
    files.forEach(file => {
        var temp = fs.lstatSync(path.join(dir, file));
        if (temp.isDirectory()) {
            scannerFileList(path.join(dir, file));
        } else {
            allFiles.push(path.join(dir, file));
        }
    });
}



scannerFileList('./iomooc');

var list = []
allFiles.forEach(file => {
    var content = fs.readFileSync(file, 'utf-8');
    var $ = cheerio.load(content);
    if (content) {
        var xiti = { type: '', title: '', radio: { A: '', B: '', C: '', D: '' } };
        xiti.type = $('.xitiList').find('.ceping-head.oneSel').text()
        xiti.title = $('.xitiList').find('.ceping-description.J_CodeLang .ceping-desc.co.clearfix p').text();
        xiti.radio.A = $('.select-wrap[opt-ind="A"] span').text();
        xiti.radio.B = $('.select-wrap[opt-ind="B"] span').text();
        xiti.radio.C = $('.select-wrap[opt-ind="C"] span').text();
        xiti.radio.D = $('.select-wrap[opt-ind="D"] span').text();
        list.push(xiti);
    }
});

console.log(list);
```