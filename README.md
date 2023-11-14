# PHP Advanced Guide <!-- omit from toc -->

- [Todo](#todo)
- [Schedule](#schedule)
- [Functions](#functions)
  - [Pages \& functions](#pages--functions)
- [PHP Coding Standard Guide](#php-coding-standard-guide)
- [Review Guide](#review-guide)
- [Remark](#remark)

## Todo

- [Object-oriented programming (OOP)](./oop/README.md)
- [Design Pattern & Principles](./design-pattern/README.md)
- [PHP MVC Framework](./mvc-framwork/README.md)

## Schedule

| Title                       | Duration (Days) |
|-----------------------------|-----------------|
| OOP                         | 2               |
| Design Pattern & Principles | 3               |
| PHP MVC Framework           | 20              |

## Functions

PHP MVC Framework က [Movie Joy](https://moviesjoyhd.to/home) Site ကို နမူနာယူပြီး project လုပ်ရမှာပါ။ Blog တွေပဲလုပ်နေရတော့ အပြောင်းအလဲ ဖြစ်သွားအောင် Movie site လုပ်ခိုင်းတာပါ။ Movie မှ မဟုတ်ဘူး Blog နဲ့ ပုံစံတူ ဘယ် site မဆိုလုပ်ခွင့်ရှိပါတယ်။ သူ့မှာပါတဲ့ Functions & Design အားလုံးတထပ်တည်းတူအောင်လုပ်စရာမလိုပါဘူး။ အောက်မှာပြောထားတဲ့ အချက်တွေ အဓိက ပါရင်ရပါပြီ။ Validation, file uploading, batch, etc. ကတော့ သက်ဆိုင်ရာ tasks ကိုရောက်တဲ့အခါ instruction ပေးပါလိမ့်မယ်။

### Pages & functions

| URI               | Page                 | Description                                                         |
|-------------------|----------------------|---------------------------------------------------------------------|
| /                 | Movie List (or) Home | The page to show movies by pagination. Add search if you've a time. |
| /movies/{id}      | Movie Detail         | The page to show specific movie.                                    |
| /movies/create    | Movie Create         | The page to create a movie.                                         |
| /movies/{id}/edit | Movie Edit           | The page to edit the movie.                                         |
| /movies/{id}      | Movie Delete         | This is just route to delete a movie.                               |
| /users            | User List            | The page to show users by pagination using html table.              |
| /users/create     | User Create          | The page to create a user.                                          |
| /users/{id}/edit  | User Edit            | The page to edit the user.                                          |
| /users/{id}       | User Delete          | This is route to delete user.                                       |
| /users/import     | User Import as CSV   | The Is route to import multiple user as CSV file.                   |
| /users/export     | User Export as CSV   | The Is route to export multiple user as CSV file.                   |



## PHP Coding Standard Guide

Coding Standard က [ဒါ](https://github.com/piotrplenik/clean-code-php) သုံးပါမယ်။ လိုရင်အနှစ်ချုပ်ကတော့ 
- variable, function, method, class တွေက meaningful ဖြစ်ရပါတယ်။ အတိုကောက်မရေးရပါ။
- Dry(Don't Repeat yourself) Code ဖြစ်ရမယ်။ တူညီတဲ့ Code ကိုထပ်ခါ၂ မရေးရပါ။
- Maintainable Code ဖြစ်ရမယ်။ Solid Design Principle ကိုလိုက်နာရမယ်။

## Review Guide

- Review စစ်မယ့်သူက OOP နဲ့ သတ်မှတ်ထားတဲ့ Design Pattern & Principle ကိုသိနေမှရပါတယ်။ ဒါမှ Review စစ်တဲ့အခါ အမှားအမှန်ကို စစ်နိင်မှာပါ။
- Project မှာတော့ Tasks တခုစီမှာ Todo, Steps, Testing ဆိုပြီး (၃) ပိုင်းရှိပါတယ်။ Todo က ဘာလုပ်ရမယ်ဆိုတာ အနှစ်ချုပ်ပြောတာပါ။ Steps ကတော့ Todo ကိုတဆင့်ချင်း ဘယ်လိုလုပ်ရမယ်ပြောတာပါ။ Testing ကတော့ လုပ်ထားတဲ့ Steps ကိုဘယ်လိုစစ်ရမယ်ပြောတာပါ။ Reviewer ကို ရလာတဲ့ Result ကို Testing ပြောထားတဲ့အတိုင်း မှန်မမှန် စစ်ရင်ရပါပြီ။ Task တခုပြီးတိုင်း တခါစစ်ပါ။ eg. Auto loading Classes ပြီးရင်စစ်မယ်။ Routing ပြီးရင်စစ်မယ်။

## Remark

PHP Advanced Guide က အခုမှ ပထမဆုံး စလုပ်တာဖြစ်တဲ့အတွက် လိုအပ်ချက်တွေရှိနိုင်ပါတယ်။ အကြုံပြုချင်တာ, မေးချင်တာရှိရင် Thet Minn Htun (thetminnhtun@metateammyanmar.com) ကိုတိုက်ရိုက်မေးနိုင်ပါတယ်။