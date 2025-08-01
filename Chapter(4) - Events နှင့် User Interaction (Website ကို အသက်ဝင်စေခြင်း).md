
#### Content

1. Events & Event Listeners
2. Event Propagation (Bubbling & Capturing) 
3. Event Delegation Concept

---

အခုဆိုရင် ကျွန်တော်တို့ style တွေပြောင်းတာ၊ Element တွေ ထည့်တာ ပြင်တာတွေ လုပ်တတ်လာပြီလို့ ယူဆပါတယ်။ ဒါပေမဲ့ အခုထိက သူက သူ့ဘာသာသူ ရပ်နေတုန်းပဲ။ User က ခလုတ်တစ်ခုကို **နှိပ်လိုက်မှ**၊ ပုံတစ်ပုံပေါ်ကို mouse **တင်လိုက်မှ**၊ keyboard မှာ ခလုတ်တစ်ခု **ရိုက်လိုက်မှ** တစ်ခုခုပြန်လုပ်တတ်အောင် "အသက်" သွင်းရပါမယ်။

ဒီလို User ရဲ့ လုပ်ဆောင်ချက်တွေကို JavaScript တုံ့ပြန်လုပ်ဆောင်တာကို User Interaction လို့ခေါ်ပါတယ်။

### 1. Events နှင့် Event Listeners

##### # Event ဆိုတာ ဘာလဲ?

ရိုးရှင်းအောင်ပြောရရင် Event ဆိုတာ web page ပေါ်မှာ ဖြစ်ပျက်သွားတဲ့ "ဖြစ်စဉ်" သို့မဟုတ် "လုပ်ဆောင်ချက်" တစ်ခုခုပါပဲ။ ဥပမာ -

- **`click`**: User က mouse နဲ့ တစ်ခုခုကို နှိပ်လိုက်ခြင်း။
    
- **`mouseover`**: User က mouse ကို element တစ်ခုပေါ် တင်လိုက်ခြင်း။
    
- **`mouseout`**: User က mouse ကို element တစ်ခုပေါ်ကနေ ပြန်ရွှေ့လိုက်ခြင်း။
    
- **`keydown`**: User က keyboard က ခလုတ်တစ်ခုကို ဖိနှိပ်လိုက်ခြင်း။
    
- **`keyup`**: User က ဖိထားတဲ့ keyboard ခလုတ်ကို ပြန်လွှတ်လိုက်ခြင်း။
    
- **`submit`**: User က form တစ်ခုကို submit လုပ်လိုက်ခြင်း။
    
- **`scroll`**: User က page ကို အပေါ်အောက် scroll ဆွဲခြင်း။

ဒါတွေအားလုံးက JavaScript ကနေ နားထောင်လို့ရတဲ့ "ဖြစ်စဉ်" (Events) တွေပါပဲ။

##### `addEventListener()` ကို အသုံးပြုပြီး Event တွေကို ဘယ်လိုနားထောင်မလဲ။

Event တစ်ခုဖြစ်လာတာကို "နားထောင်" ဖို့အတွက် ကျွန်တော်တို့မှာ "နားထောင်သူ" (Listener) တစ်ယောက် လိုအပ်ပါတယ်။ JavaScript မှာတော့ အဲ့ဒီနားထောင်သူကို `addEventListener()` ဆိုတဲ့ method နဲ့ ခန့်အပ်ရပါတယ်။

သူ့ကိုသုံးပုံက ရှင်းပါတယ်- **"ဘယ် Element ကို၊ ဘာ Event ဖြစ်ရင်၊ ဘာလုပ်ရမလဲ"** ဆိုပြီး ပြောလိုက်တာပါပဲ။

**ဥပမာ:** ခလုတ်တစ်ချက်နှိပ်ရင် "Hello World" လို့ log ထုတ်ပြတဲ့ program ရေးကြည့်ရအောင်။

**HTML Code :**

```
<button id="myButton">Click Me</button>
```

**Javascript Code :**

```
const btn = document.getElementById('myButton');

btn.addEventListener('click', function() {
    console.log('Button was clicked! Hello World!');
});
```

ဒါဆိုရင် "Click Me" ခလုတ်ကို နှိပ်လိုက်တိုင်း browser ရဲ့ console မှာ "Button was clicked! Hello World!" ဆိုပြီး ပေါ်လာပါလိမ့်မယ်။

##### # `event` Object ဆိုတာ ဘာလဲ? ( event.target က ဘယ်လောက်အသုံးဝင်လဲ။ )

`addEventListener` ထဲက function ကို အလုပ်လုပ်ခိုင်းလိုက်တဲ့အခါ၊ browser က အဲ့ဒီ function ဆီကို ဖြစ်စဉ်နဲ့ပတ်သက်တဲ့ အချက်အလက်အပြည့်အစုံပါတဲ့ object တစ်ခု လက်ဆောင်ထည့်ပေးလိုက်ပါတယ်။ အဲ့ဒါကို **`event` object** လို့ခေါ်ပါတယ်။

ဒီ object ထဲမှာ event ဖြစ်သွားတဲ့အချိန်၊ mouse ရဲ့ coordinates စတဲ့ အချက်အလက်တွေ အများကြီးပါတယ်. အဲ့ဒီထဲကမှ အသုံးဝင်ဆုံးနဲ့ အရေးအကြီးဆုံးကတော့ **`event.target`** ပါ။

**`event.target`** ဆိုတာ **"Event က ဘယ် Element အတိအကျပေါ်မှာ စတင်ဖြစ်ပွားခဲ့တာလဲ"** ဆိုတာကို လက်ညှိုးထိုးပြတဲ့ property ပါ။

**Javascript Code :**

```
btn.addEventListener('click', function(event) { 

    console.log(event);
    console.log(event.target);
    
    event.target.textContent = 'Clicked!';
});
```

`event.target` ရဲ့ အစွမ်းကို နောက် شوي Event Delegation မှာ ပိုပြီးရှင်းရှင်းလင်းလင်းမြင်ရပါလိမ့်မယ်။

---

### 2. Event Propagation (Bubbling & Capturing) - အသေးစိတ်လေ့လာခြင်း

ဒါက နည်းနည်းအဆင့်မြင့်ပေမယ့် အရမ်းအရေးကြီးတဲ့ concept တစ်ခုပါ။ Event တစ်ခုဖြစ်လာတဲ့အခါ အဲ့ဒီ event က DOM Tree ထဲမှာ ခရီးသွားပါတယ်။ ဒီလိုခရီးသွားတာကို Propagation လို့ခေါ်ပြီး ပုံစံနှစ်မျိုးရှိပါတယ်။

**HTML Code :**

```
<div id="grandparent">
    <div id="parent">
        <button id="child">Click Me</button>
    </div>
</div>
```

**# Event တစ်ခုက DOM Tree ထဲမှာ ဘယ်လိုခရီးသွားလဲ။**

ကိုယ်က `child` ဆိုတဲ့ ခလုတ်လေးကို နှိပ်လိုက်တယ် ဆိုပါစို့။ Event က အဆင့် ၃ ဆင့်နဲ့ ခရီးသွားပါတယ်။

1. **Capturing Phase:** Event က DOM Tree ရဲ့ အပေါ်ဆုံး (`window`) ကနေ အောက်ကို (`child` ဆီသို့) တဆင့်ချင်း ဆင်းလာပါတယ်။ (`window` -> `document` -> `html` -> `body` -> `grandparent` -> `parent` -> `child`)။
    
2. **Target Phase:** Event က သူ့ရဲ့ မူလပစ်မှတ် (`child`) ဆီကို ရောက်သွားပါတယ်။
    
3. **Bubbling Phase:** Event က ပစ်မှတ်ကနေ အပေါ်ဆုံး (`window` ဆီသို့) ပြန်ပြီး တဆင့်ချင်း တက်သွားပါတယ်။ (`child` -> `parent` -> `grandparent` -> `body` -> `html` -> `document` -> `window`)။


**# Bubbling (အောက်မှ အပေါ်သို့) နှင့် Capturing (အပေါ်မှ အောက်သို့) ကွာခြားချက်**

- **Capturing (Top-down):** ဖြစ်စဉ်က အပြင်ကနေ အတွင်းကိုဝင်လာတာပါ။ ဒါကို သုံးတာ အရမ်းရှားပါတယ်။ `addEventListener` မှာ တတိယ argument အဖြစ် `{ capture: true }` ထည့်ပေးမှ ဒီ phase ကို နားထောင်လို့ရပါတယ်။
    
- **Bubbling (Bottom-up):** ဖြစ်စဉ်က အတွင်းကနေ အပြင်ကို ပူဖောင်းလေးလို တက်သွားတာပါ။ ဒါက **default (ပုံမှန်)** အပြုအမူဖြစ်ပြီး ကျွန်တော်တို့ အသုံးအများဆုံးပါပဲ။ ခလုတ် (`child`) ကို နှိပ်လိုက်ရင် `child` ရဲ့ click event အရင်အလုပ်လုပ်မယ်၊ ပြီးရင် သူ့မိဘ `parent` ရဲ့ click event အလုပ်လုပ်မယ်၊ ပြီးမှ `grandparent` ရဲ့ click event အလုပ်လုပ်မှာပါ။

**`event.stopPropagation()` ကို ဘယ်လိုအခြေအနေမှာ သုံးမလဲ။**

အပေါ်က Bubbling သဘောတရားအရ `child` ကို နှိပ်ရင် `parent` နဲ့ `grandparent` ရဲ့ click event တွေပါ အလိုလို အလုပ်လုပ်သွားနိုင်ပါတယ်။

တစ်ခါတလေမှာ ဒီလိုမဖြစ်စေချင်ပါဘူး။ "ငါ့ကိုနှိပ်ရင် ငါ့အလုပ်ပဲလုပ်၊ ငါ့အကြောင်းကို အပေါ်က (parent တွေ) ကို သွားမပြောနဲ့" ဆိုပြီး event ရဲ့ ခရီးကို လမ်းမှာတင် ရပ်တန့်ချင်တဲ့အခါ **`event.stopPropagation()`** ကို သုံးပါတယ်။

**Javascript Code :**

```
const parent = document.getElementById('parent');
const child = document.getElementById('child');

parent.addEventListener('click', function() {
    console.log('Parent Clicked!');
});

child.addEventListener('click', function(event) {
    event.stopPropagation(); // ဒီနေရာမှာ event ရဲ့ bubble တက်သွားတာကို ရပ်တန့်လိုက်တယ်
    console.log('Child Clicked!');
});
```

ဒီ code မှာ `child` ခလုတ်ကိုနှိပ်ရင် "Child Clicked!" ဆိုတာပဲ ပေါ်လာပြီး "Parent Clicked!" ဆိုတာ ပေါ်လာတော့မှာ မဟုတ်ပါဘူး။ `stopPropagation()` က event ကို `parent` ဆီဆက်မသွားအောင် တားလိုက်လို့ပါပဲ။

--- 

### 3. Event Delegation ဆိုတဲ့ concept ကို အကြမ်းဖျင်းမိတ်ဆက်ခြင်း

ဒါက အပေါ်မှာပြောခဲ့တဲ့ **Bubbling** နဲ့ **`event.target`** တို့ရဲ့ အစွမ်းကို ပေါင်းစပ်ထားတဲ့ အလွန်အစွမ်းထက်ပြီး performance ကောင်းတဲ့ technique တစ်ခုပါ။

Problem:** သင့်မှာ `<li>` item အခု ၁၀၀ ပါတဲ့ စာရင်းတစ်ခုရှိတယ် ဆိုပါစို့။ `<li>` တစ်ခုချင်းစီကို click လုပ်ရင် သူ့အရောင်ပြောင်းချင်တယ်။ `<li>` ၁၀၀ လုံးကို `addEventListener` ၁၀၀ လုံး တပ်မလား? ဒါက performance မကောင်းပါဘူး။

**Event Delegation နဲ့ ဖြေရှင်းခြင်း:** `<li>` တစ်ခုချင်းစီကို listener တပ်မယ့်အစား၊ အဲ့ဒီ `<li>` အားလုံးရဲ့ **Parent ဖြစ်သူ (`<ul>`) ကိုပဲ listener တစ်ခုတည်း** တပ်လိုက်ပါ။

Bubbling သဘောတရားအရ ဘယ် `<li>` ကို နှိပ်နှိပ်၊ event က သူ့ parent `<ul>` ဆီကို တက်လာမှာပါပဲ။ အဲ့ဒီအချိန်မှာ `<ul>` မှာ တပ်ထားတဲ့ listener က `event.target` ကိုသုံးပြီး "အခု event က ဘယ် `<li>` အတိအကျဆီက လာတာလဲ" ဆိုတာကို စစ်ဆေးပြီး သက်ဆိုင်တဲ့အလုပ်ကို လုပ်ခိုင်းလိုက်ရုံပါပဲ။

**HTML Code :**

```
<ul id="itemList">
    <li>Item 1</li>
    <li>Item 2</li>
    <li>Item 3</li>
</ul>
```

**JavaScript (Event Delegation):**

```
const itemList = document.getElementById('itemList');

itemList.addEventListener('click', function(event) {
    if (event.target.tagName === 'LI') {
        event.target.style.color = 'red';
        console.log(event.target.textContent + ' was clicked!');
    }
});
```

ဒါက ဘာလို့ အဆင်ပြေတာလဲ?

1. **Performance:** Listener ၁၀၀ တပ်မယ့်အစား ၁ ခုပဲတပ်ရလို့ မှတ်ဉာဏ်သုံးစွဲမှု အရမ်းသက်သာတယ်။

2. **Dynamic Elements:** နောက်မှ JavaScript နဲ့ `<li>` အသစ်တွေ ထပ်ထည့်ရင်တောင် အဲ့ဒီ `<li>` အသစ်တွေအတွက် listener အသစ်ထပ်တပ်ပေးစရာမလိုဘဲ အလိုလို အလုပ်လုပ်ပြီးသားဖြစ်နေမှာပါ။

ဒါကြောင့် Event Delegation ဆိုတာ interactive ဖြစ်တဲ့ application ကြီးတွေရေးတဲ့အခါ မရှိမဖြစ် အရေးပါတဲ့ နည်းပညာတစ်ခုပဲ ဖြစ်ပါတယ်။
