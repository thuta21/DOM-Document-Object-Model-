
#### Contents

1. `getElementById()`
2. `getElementByClassName()`
3. `getElementsByTagName()`
4. `querySelector() & querySelectorAll()`

---

ဒါဆို "DOM ဆိုတာဘာလဲ" ကိုလည်း အကျဥ်းချုပ် သဘောပေါက်လောက်ပြီလို့ထင်ပါတယ်။ လက်တွေ့စမ်းကြည့်ရအောင်။

စမ်းတော့မယ်ဆိုရင် ပထမဆုံး IDE မှာ `index.html` နဲ့ `index.js` ဆိုပြီး HTML file နဲ့ Javascript File ၂ခု အရင်တည်ဆောက်ထားရပါမယ်။ 

```
mkdir example-page
cd example-page

touch index.html
touch index.js
```

---

### 1. `getElementById()` - မှတ်ပုံတင်နံပါတ်နဲ့ ရှာသလိုပဲ

ဒါကတော့ အရှင်းဆုံးနဲ့ အတည့်ဆုံးနည်းလမ်းပါ။ Website တစ်ခုမှာ `id` ဆိုတာ လူတစ်ယောက်ရဲ့ မှတ်ပုံတင်နံပါတ်လိုပဲ၊ တစ်ခုတည်းပဲ ရှိရမယ်လို့ သတ်မှတ်ထားတယ်။ ဒါကြောင့် `id` နဲ့ရှာတာက အရမ်းတိကျပြီး မြန်ပါတယ်။

Usage : Usage : `document.getElementsById('<Add ID>')`

**HTML Code :**

```
<h1 id="main-heading">My Website</h1>
```

**Javascript Code :**

```
// 'main-heading' ဆိုတဲ့ မှတ်ပုံတင်နံပါတ်နဲ့ကောင်ကို သွားရှာခိုင်းလိုက်မယ် 
const heading = document.getElementById('main-heading'); 

// ရှာတွေ့ပြီဆိုတော့ သူ့ကို အရောင်ပြောင်းခိုင်းမယ် 
heading.style.color = 'blue';
```

ဒါဆိုရင် Website ပေါ်က "My Website" ဆိုတဲ့ စာသားကြီး အပြာရောင်ဖြစ်သွားတာကို တွေ့ရပါလိမ့်မယ်။

---

### 2. `getElementsByClassName()` - နာမည်တူတဲ့ သူတွေ အကုန်ထွက်!

Class ဆိုတာက ကျတော့ `id` လိုမဟုတ်ပဲ နာမည်ပြောင်ပေးထားသလိုပဲ။ Elements အများကြီးကို class တစ်ခုထဲပေးထားလို့ရတယ်။ ဒီ Method က ကျတော့ class နာမည်တူတဲ့ element တွေ အကုန်သွားခေါ်ပေးပါတယ်။

Usage : `document.getElementsByClassName('<Add Class Name>')`

**HTML Code :**

```
<ul>
    <li class="fruit">Apple</li>
    <li>Car</li>
    <li class="fruit">Orange</li>
</ul>
```

**Javascript Code :**

```
const fruitItems = document.getElementsByClassName('fruit');

for (let i = 0; i < fruitItems.length; i++) {
    fruitItems[i].style.fontWeight = 'bold';
}
```

ရလဒ် အနေနဲ့က "Apple" နဲ့ "Orange" က Bold ဖြစ်သွားမှာပါ။ 

---

### 3. `getElementsByTagName()` - HTML Tag တွေနဲ့ ရှာ

ဒါကလည်း အပေါ်က `getElementsByClassName` နဲ့ ခပ်ဆင်ဆင်ပါပဲ။ ဒါပေမဲ့ class နာမည်အစား HTML Tag နာမည် (ဥပမာ - `p`, `li`, `div`) နဲ့ ရှာတာပါ။ "စာပိုဒ် (`<p>`) တွေအကုန်လုံး လာခဲ့" ဆိုပြီး ခေါ်သလိုမျိုးပေါ့။ သူက `HTMLCollection` တစ်ခုလုံး ပြန်ပေးပါတယ်။

Usage : `document.getElementsByTagName('tag-name');`

---

### 4. `querySelector() & querySelectorAll()`

အပေါ်က method တွေက အဆင်ပြေပေမယ့် တစ်ခါတလေကျရင် "ဟို `div` ထဲက ဒုတိယ `p` tag" ဆိုတာမျိုး၊ ပိုပြီးတိတိကျကျ ရှာချင်တဲ့အခါ အလုပ်ရှုပ်နိုင်တယ်။

ဒီလိုအခြေနေမျိုးအတွက်ဆိုရင် `querySelector()` နဲ့ `querySelectorAll()` တို့က လူသုံးအများဆုံးဖြစ်လာပါတယ်။

Usage : document.querySelector('selector');

##### # `querySelector()`

ဒီ `querySelector()` သုံးတဲ့နေရာမှာ element က `id` ပေးထားရင် method ထဲမှာ `#` ထည့်ရမယ်။ `class` ထည့်ထားရင်တော့ `.` ထည့်ပေးရမယ်။

**HTML Code :**

```
<div id="test">
    <p class="content">First</p>
    <p class="content">Second</p>
</div>
```

**Javascript Code:**

```
const firstContent = document.querySelector('#test .content');

firstContent.style.color = 'green';
```

ဒီကုဒ်ကို စမ်းမယ်ဆိုရင် "First" က အစိမ်းရောင်ပြောင်းသွားတာ တွေ့ရမှာပါ။

##### # `querySelectorAll()`

`querySelectorAll()` မှာကတော့ element အကုန်လုံး ယူလိုက်တာပါ။ 

Usage : document.querySelectorAll('selector');

**HTML Code :**

```
<div id="test">
    <p class="content">First</p>
    <p class="content">Second</p>
</div>
```

**Javascript Code :**

```
const allContents = document.querySelectorAll('#test .content'); 

allContents.forEach(function(item) { 
    item.style.border = '1px solid gray';
});
```

ဒီတစ်ခါတော့ "First" ရော "Second" ပါ နှစ်ခုလုံး ဘောင်ခတ်ခံလိုက်ရပါလိမ့်မယ်။

ဒီလောက်ဆိုရင် Element တစ်ခုကို ဘယ်လိုလှမ်းခေါ်အသုံးပြုလဲဆိုတာ သဘောပေါက်လိမ့်မယ်လို့ထင်ပါတယ်။ နောက်သင်ခန်းစာ တစ်ခု ဆက်ရအောင်။

---
