# Adding Files
Current directory နဲ့ subdirectory တွေ မှာ ရှိနေတဲ့ all changes (new file တွေအပါအဝင်) add ချင်ရင် -

    git add .

Entire working directory မှာ ရှိတဲ့ all changes (new file, modification, deletion) တွေအားလုံး add ချင်ရင် -

    git add -A

# Working with Remotes [^0]
### Showing Your Remotes [^1]
    git remote

`-v` ထည့်ရင် reading နဲ့ writing အတွက် Git က သိမ်းထားတဲ့ URL ကိုပြပါတယ်။

    git remote -v

remote ကို shortname နဲ့တူတူ ထပ်ထည့် (add) လုပ်မယ်ဆိုရင် 

    git remote add <shortname> <url>

### Fetching and Pulling
    git fetch

`git fetch` က data တွေကို local repo ထဲ download လုပ်ရုံသာ လုပ်ပေးပြီး local မှာ ရှိနေတဲ့ pointer ကို remote ရဲ့ update ဖြစ်နေတဲ့ နေရာထိ auto မရွေ့ (automatically merge မလုပ်) ပေးပါဘူး။ [^2]

`fetch` ပြီးရင် local ပါ update ဖြစ်ဖို့အတွက် ဒီ command သုံးရပါမယ်။

    get merge <remote>/<branch-name>

ဥပမာ `get merge origin/main`

တဖက်မှာ `git pull` ကို သုံးမယ်ဆိုရင်တော့ `pull` က `fetch` + `merge` လုပ်ပေးပေမယ့် fetch လုပ်ပြီးမှာ ကိုယ်တိုင် merge လုပ်တာကိုတော့ ပိုသဘောကျပါတယ်။  

[^0]: ဒီ cheat sheet ထဲက command အများစုက (Pro Git - 2nd Edition - by Scott Chacon and Ben Straub)[https://git-scm.com/book/en/v2] ထဲကဖြစ်ပါတယ်။
[^1]: page 52
[^2]: page 92