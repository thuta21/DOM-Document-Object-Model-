
#### Contents

1. DOM Traversing
2. DOM Manipulation

---

### 1. DOM Traversing

"Traversing" ဆိုတာက ကိုယ်ရှာတွေ့ထားတဲ့ Element တစ်ခုကနေ သူ့ရဲ့အနီးအနားက ဆက်စပ် Element တွေဆီကို ခရီးသွားတာလို့ မြင်ယောင်ကြည့်လိုက်ပါ။ ပထမပိုင်းမှာ ပြောပြထားတဲ့ မိသားစု ဥပမာလိုမျိုး မိဘဆီသွားမလား၊ သားသမီးဆီသွားမလား၊ မောင်နှမဆီသွားမလားဆိုပြီး ကူးလူးသွားလာနိုင်ပါတယ်။

**HTML Code :**

```
<div class="main-content"> 
	<h2>Articles</h2> 
	<ul id="list"> 
		<li class="item">Article 1</li> 
		<li class="item" id="second-item">Article 2</li> 
		<li class="item">Article 3</li> 
	</ul> 
	<a href="#" id="link">Read More</a> 
</div>
```

**JavaScript နဲ့ `id="second-item"` ဆိုတဲ့ `<li>` ကို အရင်ရွေးလိုက်မယ်။**

**Javascript Code :**

```
const secondItem = document.getElementById('second-item');
```

အခု `secondItem` ကနေ ဘယ်တွေကို ခရီးသွားလို့ရလဲ ကြည့်ကြမယ်။

- **(`.parentElement`):** ကိုယ့်ကို အုပ်ထားတဲ့ အပေါ်က Element ဆီကို သွားတာပါ။

```
const listParent = secondItem.parentElement;

listParent.style.border = '2px solid blue';
```

`listParent` ဆိုတာ အခု "second-item" ရဲ့ parent ဖြစ်တဲ့ `<ul id="list">` ဖြစ်သွားပါပြီ။ ဒါကိုမှ border ခတ်လိုက်တာပါ။


- `.children`: ကိုယ့်ရဲ့ အောက်မှာရှိတဲ့  Element တွေအကုန်လုံးကို စာရင်းလိုက်ကြီး ပြန်ပေးပါတယ်။

```
const allListItems = listParent.children;

console.log(allListItems.length); // Output : 3
```

`listParent` (ul) ရဲ့ Children Element (li) ၃ ခုပေါ့။


- `.firstElementChild`: ပထမဆုံး သားသမီး Element ကိုပဲ ယူတာပါ။

```
const firstArticle = listParent.firstElementChild;

firstArticle.style.color = 'green';
```


- `.lastElementChild`: နောက်ဆုံး သားသမီး Element ကို ယူတာပါ။

```
const lastArticle = listParent.lastElementChild; 

lastArticle.style.color = 'red';
```


**(`.nextElementSibling`, `.previousElementSibling`):** ကိုယ်နဲ့ level တူတူမှာရှိတဲ့ ဘေးက Element တွေကို သွားတာပါ။

- `.nextElementSibling`: ကိုယ့်ရဲ့ ညာဘက်ကပ်လျက် (နောက်က) Element။

```
const thirdItem = secondItem.nextElementSibling; // "Article 3" <li> ကိုရပါမယ်။
```


- `.previousElementSibling`: ကိုယ့်ရဲ့ ဘယ်ဘက်ကပ်လျက် (ရှေ့က) Element။

```
const firstItem = secondItem.previousElementSibling; // "Article 1" <li> ကိုရပါမယ်။
```

ဒီ property တွေကို သုံးပြီး DOM Tree ထဲမှာ လွတ်လွတ်လပ်လပ် သွားလာနိုင်ပါပြီ။

---

### 2. DOM Manipulation (ပြုပြင်ပြောင်းလဲခြင်း)

ဒါကတော့ အဓိကအပိုင်းပါပဲ။ Element တွေကို တကယ် ပြုပြင်ပြောင်းလဲတော့မှာပါ။

##### # Content ပြောင်းခြင်း (`.innerHTML` vs `.textContent`)

Element တစ်ခုရဲ့ အတွင်းထဲက စာသားကို ပြောင်းလဲတာပါ။ Method နှစ်ခုရှိပြီး သူတို့ရဲ့ ကွာခြားချက်ကို သိဖို့ အရမ်းအရေးကြီးပါတယ်။


- **`.textContent`**:

	- **စာသားသက်သက် (Plain Text)** ကိုပဲ အဓိကထားပါတယ်။
	- ထည့်လိုက်တဲ့ စာသားထဲမှာ `<h1>` တို့ `<strong>` တို့လို HTML tag တွေပါလာရင်တောင် အဲ့ဒါတွေကို HTML လို့မမြင်ဘဲ စာသားတွေအနေနဲ့ပဲ ဖော်ပြပေးမှာပါ။
	- **ပိုလုံခြုံပါတယ်။** User ဆီကရတဲ့ input တွေကို ပြန်ပြချင်တဲ့အခါမျိုးမှာ သုံးသင့်ပါတယ်။
	
- **`.innerHTML`**:
  
	- ဒါကတော့ **HTML Code တွေကို နားလည်ပြီး** တကယ် render လုပ်ပေးပါတယ်။
	- စာသားထဲမှာ `<strong>` tag ပါလာရင် စာလုံးကို တကယ် (bold) လုပ်ပေးပါလိမ့်မယ်။

**Javascript Code :**

```
const heading = document.querySelector('h2');

// textContent
heading.textContent = 'Latest <i>Articles</i>';


// innerHTML
heading.innerHTML = 'Latest <i>Articles</i>';
```

##### # Attribute ပြောင်းခြင်း (`setAttribute`, `getAttribute`, `removeAttribute`)

Element တွေမှာရှိတဲ့ `href` (link တွေမှာ)၊ `src` (ပုံတွေမှာ)၊ `disabled` (button တွေမှာ) စတဲ့ attribute တွေကို ကိုင်တွယ်တာပါ။


- **`getAttribute('attributeအမည်')`**: ရှိပြီးသား attribute ရဲ့ တန်ဖိုးကို ဖတ်တာပါ။

```
const link = document.getElementById('link');

const linkDestination = link.getAttribute('href');

console.log(linkDestination); // "#" ဆိုပြီး ပြပါလိမ့်မယ်။
```


- **`setAttribute('attributeအမည်', 'တန်ဖိုး')`**: Attribute အသစ်တစ်ခုထည့်တာ ဒါမှမဟုတ် ရှိပြီးသားတစ်ခုကို တန်ဖိုးအသစ်ပြောင်းတာပါ။

```
const link = document.getElementById('link');

link.setAttribute('href', 'https://www.google.com');

link.setAttribute('target', '_blank');
```


- **`removeAttribute('attributeအမည်')`**: Attribute တစ်ခုလုံးကို ဖယ်ရှားလိုက်တာပါ။

```
link.removeAttribute('href');
```

##### # CSS Style ပြောင်းခြင်း (`.style`, `.classList`)

Element တစ်ခုရဲ့ ဒီဇိုင်းကို JavaScript ကနေ ပြောင်းလဲတာပါ။ နည်းလမ်းနှစ်ခုရှိပြီး `.classList` က ပိုပြီး စနစ်ကျပါတယ်။

`.style` property:

- ဒါက Element တစ်ခုကို **JavaScript ထဲကနေ တိုက်ရိုက်** CSS style တစ်ခုချင်းစီကို လိုက်ပြောင်းတာပါ။ HTML မှာ inline-style `style="..."` ထည့်လိုက်သလိုပါပဲ။

- သတိချပ်ဖို့က CSS property `background-color` ကို JS မှာ `style.backgroundColor` (camelCase) နဲ့ရေးရပါတယ်။

```
const secondItem = document.getElementById('second-item');
secondItem.style.backgroundColor = 'yellow';
secondItem.style.padding = '10px';
```

`.classList` (ပိုကောင်းပြီး စနစ်ကျသောနည်းလမ်း):

- JavaScript ထဲမှာ style တွေကို တစ်ခုချင်းလိုက်ရေးတာက code တွေကို ရှုပ်စေပါတယ်။ ပိုကောင်းတဲ့နည်းကတော့ လိုချင်တဲ့ style တွေကို CSS ဖိုင်ထဲမှာ class တစ်ခုအနေနဲ့ ကြိုရေးထားပြီး JavaScript ကနေ အဲ့ဒီ class ကို လိုအပ်သလို **ထည့်လိုက်/ဖြုတ်လိုက်** လုပ်တာပါပဲ။

- **`.classList.add('classအမည်')`**: သတ်မှတ်ထားတဲ့ class ကို ထည့်ပေးပါတယ်။

**CSS Code :**

```
/* In style.css */

.highlight {
    background-color: lightblue;
    font-weight: bold;
    border-radius: 5px;
}
```

**Javascript Code :**

```
secondItem.classList.add('highlight');
```


- **`.classList.remove('classအမည်')`**: ရှိနေတဲ့ class ကို ဖယ်ရှားပေးပါတယ်။

**Javascript Code :**

```
secondItem.classList.remove('highlight');
```


- **`.classList.toggle('classအမည်')`**: မီးခလုတ်လိုပါပဲ။ class ရှိနေရင် ဖယ်ပေးတယ်။ မရှိသေးရင် ထည့်ပေးတယ်။ Dark mode ခလုတ်လိုမျိုးတွေမှာ အရမ်းအသုံးဝင်ပါတယ်။

**Javascript Code :**

```
secondItem.classList.toggle('highlight');
```

##### # Element အသစ်ဖန်တီးခြင်းနှင့် ဖယ်ရှားခြင်း

Page မှာ မရှိသေးတဲ့ Element တွေကို JavaScript ကနေ ဖန်တီးပြီး ထည့်နိုင်သလို၊ မလိုချင်တဲ့ Element တွေကိုလည်း ဖယ်ရှားနိုင်ပါတယ်။

- **`createElement('tagအမည်')`**: Element အသစ်တစ်ခုကို လေထဲမှာ ဖန်တီးလိုက်တာပါ။ Page ထဲကိုတော့ မရောက်သေးပါဘူး။

**Javascript Code :**

```
const newListItem = document.createElement('li');
```


- **`appendChild(element)`**: ဖန်တီးထားတဲ့ Element အသစ်ကို မိဘ Element တစ်ခုရဲ့ **သားသမီးတွေထဲက နောက်ဆုံးတစ်ယောက်** အဖြစ် သွားပေါင်းထည့်တာပါ။

**Javascript Code :**

```
newListItem.textContent = 'Article 4';
newListItem.classList.add('item');

const list = document.getElementById('list');
list.appendChild(newListItem);
```


- **`removeChild(element)`**: မိဘ Element ကိုပြောပြီး သူ့ရဲ့ သားသမီး Element တစ်ခုကို ဖယ်ရှားခိုင်းတာပါ။ **(ကိုယ့်ဘာသာကိုယ် ဖျက်လို့မရပါ၊ မိဘကနေတစ်ဆင့် ဖျက်ရပါတယ်)**

**Javascript Code :**

```
const itemToRemove = document.getElementById('second-item');
const itsParent = itemToRemove.parentElement;

itsParent.removeChild(itemToRemove);
```

---