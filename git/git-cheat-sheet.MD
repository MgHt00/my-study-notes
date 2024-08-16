# Git Cheat Sheet
| Table of Content      | Description |
| ----------- | ----------- |
| [Adding Files](#adding-files) | - |
[Working with Remotes](#working-with-remotes-1)| [Showing](#showing-your-remotes-2), [fetching & pulling](#fetching-and-pulling), [pushing](#pushing), [inspecting](#inspecting-a-remote), and [renaming a remote](#renaming-a-remote)
| [Tagging](#tagging-4) | [Listing](#listing-tags), [creating](#creating-tag), [sharing](#sharing-tags), and [deleting tag](#deleting-tags); [tagging later](#tagging-later) |
| [Git Branching](#git-branching) | [Creating a New Branch](#creating-a-new-branch-5), [Switching Branches](#switching-branches) |

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

    git merge <remote>/<branch-name>

ဥပမာ `git merge origin/main`

တဖက်မှာ `git pull` ကို သုံးမယ်ဆိုရင်တော့ `pull` က `fetch` + `merge` လုပ်ပေးပေမယ့် fetch လုပ်ပြီးမှာ ကိုယ်တိုင် merge လုပ်တာကိုတော့ ပိုသဘောကျပါတယ်။  

### Pushing

        git push <remote> <branch>

`master` branch ကို `origin` server ဆီ push လုပ်မယ် - 

        git push origin master

### Inspecting a Remote

        git remote show <remote>

### Renaming a Remote

        git remote rename <old-name> <new-name>

# Tagging [^3]
### Listing Tags

        git tag

v1.1 နဲ့ စတဲ့ tag တွေကို ရှာမယ် - 

        git tag -l "V1.1*"

Listing အတွက် `-l` (သို့) `--list` option လိုပါတယ်။

### Creating Tag

Lightweight tag နဲ့ annotated tag ၂ မျိုးရှိပြီး ၊ annotated tag က Git database ထဲမှာ full object အနေနဲ့ သိမ်းပြီး tagger name, email, date, tagging message တို့ပါပြီး GN Privacy Guard (GPG) နဲ့ signed and verified လုပ်လို့်ရပါတယ်။ 

#### Annotated Tags

        git tag -a <tag-name> -m <"message">

eg. `git tag -a v1.4 -m "my version 1.1"` -m က tagging message ကို specify လုပ်ပြီး tag နဲ့ အတူ သိမ်းပါတယ်။  annotated tag မှာ message specify မလုပ်မိရင် မရ မက ထည့်ခိုင်းဖို့ Git က editor ဖွင့်ပေးပါလိမ့်မယ်။  

#### Lightweight Tags

        git tag <tag-name> 

ဒါပါပဲ။

### Tagging Later

နောက်ကားနဲ့ လိုက် tag ချင်တယ်ဆိုရင် commit checksum ကိုသိဖို့လိုလိမ့်မယ်၊ ဒါကို အရင်သုံး...

        git log --pretty=online

ကျလာတဲ့ထဲက checksum ကို ရှာ 

        git tag -a <tag-name> <checksum>

Lightweight tag ပဲသုံးချင်ရင် `-a` မထည့်ရုံပဲပေါ့။  

### Sharing Tags

Tag တွေကို create လုပ်ရုံနဲ့ အတောင်ပံပေါက်ပြီး remote ဆီတက်သွားမှာ မဟုတ်သလို ၊ လိုင်းကားမှာခိုစီးသလို git commit မှာ အချောင်ကပ်ပါသွားမှာ မဟုတ်တဲ့အတွက် remote မှာလဲ ကိုယ့်ရဲ့ လှတပတ tag တွေရှိနေစေချင်ရင် တွန်းတင် (push) လုပ်ပေးရပါမယ်။  

        git push <remote-name> <tag-name>

အားအားရှိ tag တွေအများကြီးလုပ်ထားလို့ တစ်ခုချင်း တွန်းရမှာ မောရင် tag အကုန်လုံးကိုသာ တစ်ခါတည်း push ...

        git push <remote-name> --tags

ဒီ command က lightweight ရော annotated ပါ တွန်းမှာမို့လို့ ၊ ပေါ့ပေ့ါပါးပါး lightweight ပဲ တွန်းပါ သွားလုပ်လို့ မရပါဘူး။  

### Deleting Tags

Local repo မှာ ရှိတဲ့ tag ကို ဖျက်မယ်ဆိုရင် 

        git tag -d <tag-name>

ထုံးစံအတိုင်း local မှာ ဖျက်လို့ ခြေရာလက်ရာက remote မှာ ဟောသလို ဟောသလို မပျောက်တဲ့ အတွက် - 

        git push origin :refs/tags/<tag-name>

မှတ်ရတာ ရှုပ်ပါတယ် ၊ ဖျက်မနေပါနဲ့တော့ ....  

လွယ်တာလေးလဲ ရှိပါတယ် - 

        git push <remote-name> --delete  <tag-name>

# Git Branching
### Creating a New Branch [^4]

Branch အသစ်လုပ်ချင်ရင် - 

        git branch <branch-name>

`git branch` က branch အသစ်ကိုပဲ ဖန်တီးပြီး HEAD ကိုတော့ မရွေ့ပေးပါဘူး။  HEAD က ဘယ်ကို ထိုးနေလဲ သိချင်ရင် 

        git log --oneline --decorate

### Switching Branches

ရှိပြီးသား branch ကို switch လုပ်ချင်ရင် 

        git checkout <exiting-branch-name>


[^0]: ဒီ cheat sheet ထဲက command အများစုက (Pro Git - 2nd Edition - by Scott Chacon and Ben Straub)[https://git-scm.com/book/en/v2] ထဲကဖြစ်ပါတယ်။
[^1]: page 52
[^2]: page 92
[^3]: page 55
[^4]: page 65