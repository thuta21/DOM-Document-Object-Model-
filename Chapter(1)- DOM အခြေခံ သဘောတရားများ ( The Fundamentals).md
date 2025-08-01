
#### Contents

1. DOM ဆိုတာ ဘာလဲ? (​ Introduction to DOM )
2. DOM ရဲ့ ဖွဲ့စည်းပုံ ( Tree Structure )
3. Static Website နဲ့ Dynamic Website ကွာခြားချက်မှာ DOM က ဘယ်လိုအခန်းကဏ္ဍက ပါဝင်လဲ။

---
### **1. DOM ဆိုတာဘာလဲ? (Introduction to DOM)**

**DOM** ဆိုတာ ဘာကြီးလဲ? ရိုးရိုးလေး တွေးကြည့်ရအောင်။ **DOM** ရဲ့ အရှည်ကောက်ကတော့ **Document Object Model** လို့ခေါ်တယ်။ ဒါပေမယ့် ခက်ခက်ခဲခဲ စာလုံးတွေ ခနမေ့ထားပြီး DOM ကို "မိသားစု ဇယား" တစ်ခု အနေနဲ့ သဘောထားကြည့်လိုက်ပါ။ 

Website တစ်ခုရဲ့ HTML code တွေက မိသားစုဝင် စာရင်းတစ်ခုလိုပဲ။ ဘယ်သူက မိဘ ( parent ) | ဘယ်သူက သားသမီး ( child ) ဆိုတာ စာနဲ့ချရေးထားတာမျိုးပေါ့။ 

Browser ( Chrome, Firefox တို့လို့) က HTML code တွေကို ဖတ်လိုက်တဲ့ အခါ ဒီမိသားစုဝင်တွေရဲ့ ဆက်နွယ်တာတွေကို သဘောပေါက်လွယ်အောင် `"Tree Structure"` တစ်ခု ဆွဲလိုက်တယ်။ ဒီဟာကိုပဲ DOM လို့ခေါ်တာပါ။

ဒီနေရာမှာ Javascript လို Programming Language ကို သုံးပြီး Website က ဘယ် element ကို ၊ ဘယ် စာသားတွေ အရောင်ပြောင်းမယ်။ ဟိုနေရာရွေ့၊ ဒီနေရာ ဖျက် ဆိုပြီး လုပ်လို့ရသွားတယ်။

Notes: 

- **DOM (Document Object Model)** ဆိုတာ **HTML** နဲ့ **JavaScript** ကြားမှာ ချိတ်ဆက်ပေးတဲ့ **Interface (တံတား)** တစ်ခုဖြစ်ပါတယ်။

- **HTML** ကို **JavaScript** ကနေ ပြုပြင်လို့ရအောင် **Tree Structure (သစ်ပင်ပုံစံ Model)** အဖြစ် ဖန်တီးထားတာဖြစ်ပါတယ်။

- **DOM** ကို သုံးပြီး **Web Page** ပေါ်က **Element တွေကို Select, Modify, Delete, Create** လုပ်လို့ရပါတယ်။

---

### **2. DOM ရဲ့ ဖွဲ့စည်းပုံ ( The Tree Structure )**

DOM က အရာအားလုံးကို **"Node"** (နုတ်) လို့ခေါ်တဲ့ အရာတွေနဲ့ ဖွဲ့စည်းထားတယ်။ မျိုးရိုးပြဇယားမှာဆိုရင် လူတစ်ယောက်ချင်းစီလိုပေါ့။ အဓိက Node သုံးမျိုးရှိပါတယ်။

1. **Element Node:** HTML tag တွေ အားလုံး (ဥပမာ `<body>`, `<div>`, `<h1>`, `<p>`)။
    
2. **Text Node:** Element တွေရဲ့ ကြားထဲမှာရှိတဲ့ စာသားတွေ (ဥပမာ `<h1>` ထဲက "Hello World!" ဆိုတဲ့ စာသား)။
    
3. **Attribute Node:** Element တွေရဲ့ ဂုဏ်သတ္တိတွေ (ဥပမာ `<p class="info">` မှာဆို `class="info"` က attribute node ပါ)။

ဒါဆို index.html file တစ်ခု တည်ဆောက်ပြီး HTML code တစ်ခု စရေးကြည့်ရအောင်။

```
<!DOCTYPE html>
<html>
<head>
    <title>My Website</title>
</head>
<body>
    <h1 id="main-heading">Hello World!</h1>
    <p class="intro">A Paragraph.</p>
</body>
</html>
```

DOM Tree ပုံစံ:

               [document]
                   |
                 [html]
                 /    \
             [head]    [body]
               |         /   \
            [title]   [h1 id="main-heading"]   [p class="intro"]
               |             |                      |
      (Text: "My Website")  (Text: "Hello World!")   (Text: "A Paragraph.")

ကျွန်တော်တို့ ဒီ Tree Structure ကို ကြည့်ရင် 

- `<html>` က `<body>` ရဲ့ parent ။
- `<body>` က ကျတော့ `<h1>` နဲ့ `<p>` ရဲ့ parent ။
- `<h1>` နဲ့ `<p>` ကတော့ children တွေလို့ မြင်ကြည့်နိုင်ပါတယ်။

---

### **3. Static Website နဲ့ Dynamic Website ကွာခြားချက်မှာ DOM က ဘယ်လိုအခန်းကဏ္ဍက ပါဝင်လဲ။**

**Static Website (ပုံသေ Website):**

Static website များသည် server ပေါ်တွင် ကြိုတင်ရေးသားသိမ်းဆည်းထားသော HTML, CSS, JavaScript ဖိုင်များကို အသုံးပြုသူ (user) တောင်းဆိုသည့်အခါ မပြောင်းလဲပဲ ပြန်လည်ပြသပေးသော website အမျိုးအစားဖြစ်သည်။ ဆိုလိုတာက user တိုင်းအတွက် contents တွေက အတူတူပါပဲ။ 

Static Website များမှာက DOM သည် browser မှ page ကို load လုပ်သည့်အချိန်တွင် တစ်ကြိမ်သာ တည်ဆောက်တယ်။ JavaScript အနည်းငယ်ဖြင့် DOM ကို ပြောင်းလဲနိုင်သော်လည်း (ဥပမာ - image slider)၊ အခြေခံ content သည် ပြောင်းလဲသွားခြင်းမရှိပါဘူး။ DOM ၏ အဓိကအခန်းကဏ္ဍမှာ page ရဲ့ ကနဦးတည်ဆောက်ပုံကို ဖော်ပြဖို့ အတွက်သာဖြစ်ပါတယ်။

**Dynamic Website (အပြောင်းအလဲရှိသော Website):**

Dynamic website များသည် user တွေရဲ့ တောင်းဆိုမှု၊ အချိန်၊ တည်နေရာ၊ သို့မဟုတ် အခြားသော အချက်အလက်များပေါ်မူတည်၍ content များကို အချိန်နှင့်တပြေးညီ (real-time) ထုတ်လုပ်ပြောင်းလဲပေးသော website အမျိုးအစားဖြစ်ပါတယ်။ (ဥပမာ - Facebook, YouTube, e-commerce)

**DOM ၏ အဓိကအခန်းကဏ္ဍ:**

**User Interaction:** User က ခလုတ်တစ်ခုကို နှိပ်ခြင်း၊ form တစ်ခုဖြည့်စွက်ခြင်း၊ သို့မဟုတ် page ကို scroll လုပ်ခြင်းစသည့် လုပ်ဆောင်မှုများ ပြုလုပ်သည့်အခါ JavaScript က DOM ကို အသုံးပြု၍ page ရဲ့အစိတ်အပိုင်းများကို အသစ်ထပ်ထည့်ခြင်း (e.g., loading more posts)၊ ဖယ်ရှားခြင်း၊ သို့မဟုတ် ရှိပြီးသား content ကို ပြောင်းလဲခြင်း (e.g., updating a shopping cart) များ ပြုလုပ်ပါတယ်။

**Data from Server:** Server မှ data အသစ်များ (ဥပမာ - chat message အသစ်၊ notification အသစ်) ရောက်ရှိလာသည့်အခါ JavaScript က ထို data များကို DOM ထဲသို့ ထည့်သွင်း၍ page ကို refresh မလုပ်ဘဲ အလိုအလျောက် update လုပ်ပေးတယ်။

ဒီလောက်ဆို DOM အခြေခံလောက်ကို သဘောပေါက်လောက်မယ်ထင်ပါတယ်။ နောက်အပိုင်းမှာ စပြီး လက်တွေ့အသုံးချကြည့်ပါမယ်။

---

