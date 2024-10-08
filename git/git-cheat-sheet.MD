# Git Cheat Sheet
| Category      | Sub-category |
| ----------- | ----------- |
| The Basics | [Adding Files](#adding-files), [Removing Files], [Renaming Files], [Unstaging a Staged File], [Unmodifying a Modified File] |
[Working with Remotes](#working-with-remotes-1)| [Showing](#showing-your-remotes-2), [fetching & pulling](#fetching-and-pulling), [pushing](#pushing), [inspecting](#inspecting-a-remote), and [renaming a remote](#renaming-a-remote)
| [Tagging](#tagging-4) | [Listing](#listing-tags), [creating](#creating-tag), [sharing](#sharing-tags), and [deleting tag](#deleting-tags); [tagging later](#tagging-later) |
| [Git Branching](#git-branching) | [Creating a New Branch](#creating-a-new-branch-5), [Switching Branches](#switching-branches), [Creating & Switching](#creating--switching), [Divergent History](#divergent-history), [Delete a Branch](#delete-a-branch)|
|[Branching & Merging](#branching--merging6)| [Basic Merging](#basic-merging), [Fast-forward & Three-Way Merge](#fast-forward--three-way-merge), [Basic Merge Confilcts](#basic-merge-confilcts9)|
|[Branch Management](#branch-management10)|[The Basics](#tha-basics), [Changing a Branch Name](#changing-a-branch-name11), [Creating a Backup Branch](#creating-a-backup-branch12), [Deleting Commit(s)], [Creating a branch from a specific commit]|
|[Remote Branch]||

# The Basics
## Adding Files
Current directory နဲ့ subdirectory တွေ မှာ ရှိနေတဲ့ all changes (new file တွေအပါအဝင်) add ချင်ရင် -

 ```shell
 $ git add .
```

Entire working directory မှာ ရှိတဲ့ all changes (new file, modification, deletion) တွေအားလုံး add ချင်ရင် -

```shell
$ git add -A
```

## Removing Files
Git ထဲကနေ file ကို remove လုပ်ဖို့အတွက် tracked files (staging area) နေ remove လုပ်ရပါမယ်။  

`git rm` က staging area ကနေ ထုတ်ပေးတဲ့အပြင် working directory မှာပါဖျက်ပေးပါတယ်။

```shell
$ git rm Projects.MD
```

အကယ်လို့ working directory မှာ ချန်ထားပြီး git ထဲမှာ ဖျက်ချင်ရင် 

```shell
$ git rm --cached Projects.MD
```

`*.log` ကို ဖျက်ချင်ရင် (shell ရဲ့ filename expansion မှာ Git က ကိုယ်ပိုင် filename expansion ထပ်ပေါင်းတာကြောင့်)  အရှေ့မှာ `\` ခံပေးရပါတယ်။

```shell
$ git rm \*.log

$ git rm log/\*log
```
ဒုတိယ command က log directory ထဲက log နဲ့ ဆုံးတဲ့ file တွေအားလုံးဖျက်မှာပါ။  

## Renaming Files
File ကို rename လုပ်ချင်ရင် 

```shell
$ git mv old_name new_name
```
`git mv` က command ၁ ခုတည်းနဲ့ ဒီ ၃ မျိုးလုပ်ပေးပါတယ်။

```shell
$ mv old_name new_name
$ git rm old_name
$ git add new_name
```

## Unstage a Staged File
မှားပြီး staged လုပ်ထားတဲ့ file ကို staging area က ပြန်ထုတ်ချင်ရင် 

```shell
$ git restore --staged FILE.MD
```

`--staged` မထည့်ပေးလိုက်ရင် shock ရှိပါတယ်။ အကယ်လို့ လိုလိုချင်ချင် မထည့်ပေးလိုက်မိတာဆိုရင်တော့ လက်ရှိလုပ်နေတဲ့ local changes တွေအားလုံးပျောက်ပြီး နောက်ဆုံး commit လုပ်ထားတဲ့ (last staged) version ကို ပြန်ပြောင်းသွားမှာပါ။  

```shell
$ git restore FILE.MD
```

# Working with Remotes [^1]
### Showing Your Remotes [^2]
    $ git remote

`-v` ထည့်ရင် reading နဲ့ writing အတွက် Git က သိမ်းထားတဲ့ URL ကိုပြပါတယ်။

    $ git remote -v

remote ကို shortname နဲ့တူတူ ထပ်ထည့် (add) လုပ်မယ်ဆိုရင် 

    $ git remote add <shortname> <url>

### Fetching and Pulling
    $ git fetch

`git fetch` က data တွေကို local repo ထဲ download လုပ်ရုံသာ လုပ်ပေးပြီး local မှာ ရှိနေတဲ့ pointer ကို remote ရဲ့ update ဖြစ်နေတဲ့ နေရာထိ auto မရွေ့ (automatically merge မလုပ်) ပေးပါဘူး။ [^3]

`fetch` ပြီးရင် local ပါ update ဖြစ်ဖို့အတွက် ဒီ command သုံးရပါမယ်။

        $ git merge <remote>/<branch-name>

ဥပမာ `git merge origin/main`

တဖက်မှာ `git pull` ကို သုံးမယ်ဆိုရင်တော့ `pull` က `fetch` + `merge` လုပ်ပေးပေမယ့် fetch လုပ်ပြီးမှ ကိုယ်တိုင် merge လုပ်တာကိုတော့ ပိုသဘောကျပါတယ်။  

### Pushing
        $ git push <remote> <branch>

`master` branch ကို `origin` server ဆီ push လုပ်မယ် - 

        $ git push origin master


The commands `git push` and `git push origin main` are both used to upload your local commits to a remote repository, but they have some key differences in terms of their behavior:

### 1. `git push`
- **Default Behavior**: When you use `git push` without specifying any remote or branch, Git uses the default remote and branch configurations set in your repository.
- **Default Remote**: Typically, the default remote is `origin` (the one you cloned from).
- **Default Branch**: The branch you’re pushing to depends on your branch’s upstream configuration (the branch it tracks on the remote).
- **Potential for Multiple Branches**: If your current branch is configured to track a branch on the remote, `git push` will push to that branch. If there are other branches configured to push to the remote, they might be pushed as well.

### 2. `git push origin main`
- **Explicit Remote and Branch**: This command explicitly specifies that you want to push to the `main` branch on the `origin` remote.
- **Single Branch Push**: It only pushes the current state of your local `main` branch to the `main` branch on the `origin` remote.
- **More Control**: By specifying both the remote (`origin`) and branch (`main`), you have more control over exactly what gets pushed and where.

### Summary
- **`git push`**: Uses the default settings (typically `origin` and the branch you’re currently on). It pushes the changes to the upstream branch set in your repository.
- **`git push origin main`**: Explicitly pushes your current `main` branch to the `main` branch on the `origin` remote.

Using `git push origin main` is generally safer and more explicit, ensuring that you’re only pushing the branch you intend to push to the correct remote and branch.

### Inspecting a Remote

        git remote show <remote>

### Renaming a Remote

        $ git remote rename <old-name> <new-name>

# Tagging [^4]
### Listing Tags
        $ git tag

v1.1 နဲ့ စတဲ့ tag တွေကို ရှာမယ် - 

        $ git tag -l "V1.1*"

Listing အတွက် `-l` (သို့) `--list` option လိုပါတယ်။

### Creating Tag

Lightweight tag နဲ့ annotated tag ၂ မျိုးရှိပြီး ၊ annotated tag က Git database ထဲမှာ full object အနေနဲ့ သိမ်းပြီး tagger name, email, date, tagging message တို့ပါပြီး GN Privacy Guard (GPG) နဲ့ signed and verified လုပ်လို့်ရပါတယ်။ 

#### Annotated Tags

        $ git tag -a <tag-name> -m <"message">

eg. `git tag -a v1.4 -m "my version 1.1"` -m က tagging message ကို specify လုပ်ပြီး tag နဲ့ အတူ သိမ်းပါတယ်။  annotated tag မှာ message specify မလုပ်မိရင် မရ မက ထည့်ခိုင်းဖို့ Git က editor ဖွင့်ပေးပါလိမ့်မယ်။  

#### Lightweight Tags

        $ git tag <tag-name> 

ဒါပါပဲ။

### Tagging Later

နောက်ကားနဲ့ လိုက် tag ချင်တယ်ဆိုရင် commit checksum ကိုသိဖို့လိုလိမ့်မယ်၊ ဒါကို အရင်သုံး...

        $ git log --pretty=online

ကျလာတဲ့ထဲက checksum ကို ရှာ 

        $ git tag -a <tag-name> <checksum>

Lightweight tag ပဲသုံးချင်ရင် `-a` မထည့်ရုံပဲပေါ့။  

### Sharing Tags

Tag တွေကို create လုပ်ရုံနဲ့ အတောင်ပံပေါက်ပြီး remote ဆီတက်သွားမှာ မဟုတ်သလို ၊ လိုင်းကားမှာခိုစီးသလို git commit မှာ အချောင်ကပ်ပါသွားမှာ မဟုတ်တဲ့အတွက် remote မှာလဲ ကိုယ့်ရဲ့ လှတပတ tag တွေရှိနေစေချင်ရင် တွန်းတင် (push) လုပ်ပေးရပါမယ်။  

        $ git push <remote-name> <tag-name>

အားအားရှိ tag တွေအများကြီးလုပ်ထားလို့ တစ်ခုချင်း တွန်းရမှာ မောရင် tag အကုန်လုံးကိုသာ တစ်ခါတည်း push ...

        $ git push <remote-name> --tags

ဒီ command က lightweight ရော annotated ပါ တွန်းမှာမို့လို့ ၊ ပေါ့ပေ့ါပါးပါး lightweight ပဲ တွန်းပါ သွားလုပ်လို့ မရပါဘူး။  

### Deleting Tags

Local repo မှာ ရှိတဲ့ tag ကို ဖျက်မယ်ဆိုရင် 

        $ git tag -d <tag-name>

ထုံးစံအတိုင်း local မှာ ဖျက်လို့ ခြေရာလက်ရာက remote မှာ ဟောသလို ဟောသလို မပျောက်တဲ့ အတွက် - 

        $ git push origin :refs/tags/<tag-name>

မှတ်ရတာ ရှုပ်ပါတယ် ၊ ဖျက်မနေပါနဲ့တော့ ....  

လွယ်တာလေးလဲ ရှိပါတယ် - 

        $ git push <remote-name> --delete  <tag-name>

# Git Branching
### Creating a New Branch [^5]
Branch အသစ်လုပ်ချင်ရင် - 

        $ git branch <branch-name>

`git branch` က branch အသစ်ကိုပဲ ဖန်တီးပြီး HEAD ကိုတော့ မရွေ့ပေးပါဘူး။  HEAD က ဘယ်ကို ထိုးနေလဲ သိချင်ရင် 

        $ git log --oneline --decorate

### Switching Branches
ရှိပြီးသား branch ကို switch လုပ်ချင်ရင် 

        $ git checkout <exiting-branch-name>

ဒီမှာ `git log` က လက်ရှိ checkout လုပ်ထားတဲ့ branch မှာရှိတဲ့ commit history တွေကိုပဲ ပြလို့  branches အားလုံးရဲ့ log ကို မပြလို့ အားလုံးပြစေချင်ရင် 

        $ git log --all

သိချင်တဲ့ branch ကိုပဲ ရွေးပြစေချင်ရင် 

        $ git log <branch-name>

### Creating & Switching
Branch အသစ်လုပ် တန်းပြောင်း - all in one go - 

        $ git checkout -b <new-branch-name>

version 2.23 အထက်ဆိုရင် မှတ်ရတာ ပိုများအောင် အသစ်ပါတာက 

        $ git switch -c <new-branch-name>

`-c` stands for create တဲ့ ၊ b ကတော့ ဘာ stands လဲ ကိုယ်လဲမသိ

Branch ပြန်ပြောင်းမယ်ဆိုရင် 

        $ git checkout <branch-name>

### Pushing the New Branch to the Remote
အသစ်လုပ်ထားတဲ့ new branch ကို remote ဆီတွန်းဖို့ 

        $ git push <remote> <branch-name>
        
New branch လုပ်ပြီးရင် new branch ကို remote branch နဲ့ track ဖို့ အသိပေးထားတာ ကောင်း

        $ git push --set-upstream <remote> <branch-name>

### Divergent History

Commit history ကို branch pointer တွေနဲ့တူတူ history က ဘယ်ကနေ diverge ဖြစ်လာတာလဲ ကြည့်ဖို့

        $ git log --oneline --decorate --graph --all

### Delete a Branch

Safely deletes a branch, only if it has been merged:

        $ git branch -d <branch-name>

Forcefully deletes a branch, regardless of its merged status:

        $ git branch -D <branch-name>

### Deleting the Remote Branch
Remote မှာ ရှိတဲ့ branch ကို delete လုပ်ချင်ရင် 

        $ git push --delete <remote> <branch-name>



# Branching & Merging[^6]
### Basic Merging
1. ကျန်နေခဲ့မယ့် branch ဆီကို အရင်သွားပါ။ (check out the branch you wish you merge into)
2. merge ပါ။

        $ git checkout <branch-name>
        $ git merge <incoming-branch-name>

eg. `master` ထဲကို `hotfix` လာ merge ချင်ရင်

        $ git checkout master
        $ git merge hotfix

### Fast-forward & Three-Way Merge
Fast-forward merge မှာ Git က commit အသစ် မလုပ်ပဲ point ပဲရွေ့ပါတယ်။ တစ်နည်းအားဖြင့် divergent history မရှိရင် Git က fast-forward merge လုပ်ပါတယ်။  Defination အပြည့်အစုံကို စာအုပ်မှာ[^7]ဖတ်ပါ။

အကယ်လို့ history က diverged ဖြစ်နေပြီဆိုရင် Git က branch ၂ ခု မှာရှိတဲ့ ထိပ်ဖျား snapshot ၂ ခု ရယ် ၊ branch ၂ ခုလုံးရဲ့ common ancestor ရယ်သုံးပြီး simple three-way merge လုပ်ပေးမှာပါ။[^8] 

### Basic Merge Confilcts[^9]
ဘယ်ကိစ္စမဆို အစဥ်ချောမွေ့တဲ့ သဘောမရှိတဲ့ လောကကြီးမှာ Git လဲ ပါတာကြောင့် အကယ်လို့ file တစ်ခုတည်းမှာ ဟိုပြင် ဒီပြင် ၂ ခါပြင်လို့ ၂ ခု ရှိ ၊ Git က မျက်စိတွေလည်ပြီး ဘာလုပ်ရမလဲ ဖြစ်လာရင် ဒီတိုင်း merge လုပ်ချလိုက်မှာမဟုတ်ပဲ `CONFLICT` ပြလာတော့မှာပါ။  

1. merge conflict ဖြစ်ပြီး merge မလုပ်ပဲ ကျန်နေခဲ့တဲ့ file တွေကို `git status` နဲ့ ကြည့်ပါ။ `<<<<<<`, `=======`, `>>>>>>>>` Git က ဒီ conflict marker တွေနဲ့ ဘာတွေဖြစ်နေသလဲ ပြပါလိမ့်မယ်။  `<<<<<<< HEAD:` ပြနေတာက ကိုယ်သွား merge လုပ်ချင်လွန်းလို့ checkout လုပ်ထားတဲ့ branch မှာ ရှိနေတဲ့ file ပါ။   `======` ကတော့ တစ်ပိုင်းပြီးပြီပေ့ါ။  `>>>>>>` က လာပေါင်းမယ့် branch မှာ ဖြစ်နေတဲ့ ကိစ္စတွေကို ပြပါတယ်။  

2. Conflict ကို ပြေလည်ဖို့အတွက် ၊ ဖြူဖြူကိုပဲ ရွေးလိုက်ရမလား ၊ ဂျူဂျူကိုပဲ ရွေးလိုက်ရမလား ၊ ဒါမှ မဟုတ် ၂ ခုလုံး ပေါင်းလိုက်ရမလား ကိုယ်တိုင်စဥ်းစားပြီး ပြင်ဆင်ပါ။

3. Conflict ကို resolve လုပ်ပြီးပြီိဆိုရင် ပြင်စရာရှိတာ ပြင်ထားပြီးတဲ့ file တစ်ခုချင်းစီကို `git add` နဲ့ conflict resolve လုပ်ပြီးကြောင်း mark လုပ်ပါ။  

4. အခြေအနေ သိရဖို့ `git status` နဲ့ ပြန် verify လုပ်ပါ။  `All conflicts fixed but... ` ဘာညာ ပြရင် ရပါပြီ။

5. `git commit` နဲ့  happily merge လုပ်လို့ ရပါပြီ။  

                $ git status
                Edit the file
                $ git add
                $ git status
                $ git commit 

# Branch Management[^10]
### The Basics
ဘာ argument မှ မပါပဲ သုံးရင် ရှိတဲ့ branch တွေကို ပြပေးပါမယ်။

        $ git branch

Branch တစ်ခုချင်းစီမှာ ရှိတဲ့ last commit ကို ကြည့်မယ် - 

        $ git branch -v

လက်ရှိရောက်နေတဲ့ (checkout လုပ်) ထားတဲ့ branch ကို git က `*` အရှေ့မှာထားပြီး ပြပေးပြီး ၊ အခုရောက်နေတဲ့ branch နဲ့ ဘယ် branch တွေ merged လုပ်ထားလဲကို `--merged` ၊ ဘယ် branch တွေက မလုပ်ထားလဲဆိုတာကို `--no-merged` နဲ့ ကြည့်ပါလေ့ -

        $ git brach --merged

အပေါ်က command ၂ ခုက branch ကို ပြောင်း (checkout) လုပ်ပြီးမှာ ကြည့်တဲ့ command ပါ။  မပြောင်းပဲ အဝေးကနေ လှမ်းမျှော်ကြည့်ဖို့ဆိုရင် - 

        $ git checkout testing 
        // အစွမ်းပြချင်လို့ testing branch ကို အရင်ပြောင်းထားတာပါ။

        $ git branch --merged main 
        // main ကို လာ merge ထားတာ ဘယ် branch တွေရှိနေပြီးလဲဆိုတာ ကို testing branch မှာ ထိုင်နေပြီး လှမ်းရှိုးတာဖြစ်ပါတယ်။

ရှိသမျှ local ရော remote branch တွေရော စုပြုံကြည့်မယ် - 

        $ git branch --all

ပြန်ပြလာတဲ့ထဲမှာ `*` ပါတာက remote ဖြစ်ပြီး ဘာ prefix မှ မပါပဲ list လုပ်ထားတာတွေက local branch တွေပါ။ 

အဝေးရောက် remote branch တွေပဲ စိတ်ဝင်စားရင် -

        $ git branch -r

### Changing a Branch Name[^11]
History တွေကို မပြောင်း ၊ မထိပဲ brach name ပဲ ပြောင်းမယ် -

        $ git branch --move <bad-branch-name> <corrected-branch-name>

ဒီလိုပြောင်းလိုက်လို့ ဟောသလို ဟောသလို remote မှာပါလိုက်ပြောင်းမှာ မဟုတ်တဲ့အတွက် - 

        $ git push --set-upstream <remote> <corrected-branch-name>

Remote က အင်မတန်ရိုးပါတယ်။ အပေါ်က command နဲ့ branch name ပြောင်းလိုက်ပြီဆိုတာ `push` လုပ်လိုက်လို့ branch name ကို ပြောင်းလိုက်သော်ငြားလဲ အဟောင်းလေးကိုပါဆက်သိမ်းပေးထားနေလို့ ဖျက်ချင်ရင် - 

        $ git push <remote> --delete <bad-branch-name>

### Creating a Backup Branch[^12]
When a new branch is created, Git simply creates a pointer to the current commit, meaning that the new branch will have the same history and content as the branch you created if from.  This provide a snapshot or backup of the branch at that point in time.

#### Step-by-Step Process
1. Backup လုပ်ချင်တဲ့ branch ကို အရင်ပြောင်း
        
        $ git checkout <branch-name>

2. Backup အနေနတဲ့ branch အသစ်ဆောက်

        $ git branch <backup-branch-name>

   ဒါမှမဟုတ် သေချာအောင် တခါတည်း ပြောင်းကြည့်လို့လဲ ရပါ့

        $ git checkout -b <backup-branch-name>

3. Branch တွေ အားလုံး ထင်သလို အိုကေ နေပြီလား verify လုပ် -

        $ git branch

#### Revert to the Backup if Needed
မဖြစ်ချင်ပေမယ့်လဲ ဖြစ်လာမှာမို့ backup လုပ်ထားတဲ့ branch ကို အတည်ယူပြီး ပြန် restore လုပ်ဖို့ လိုလာခဲ့ရင် - 

1. Backup လုပ်ထားတဲ့ branch ကို ပြောင်း

        $ git checkout <backup-branch>

2. အဖတ်ဆည်မရတော့တဲ့ branch ကို delete လုပ် (force delete လိုဖို့များ)

        $ git branch -D <messed-up-branch>

3. Backup လုပ်ထားတဲ့ branch ကနေ branch အသစ်ပြန်ပွားယူ

        $ git checkout -b <fresh-branch>

<em>Branch ဖျက်လိုက်တာနဲ့ အသစ်ဆောက်ထားတဲ့ ကိစ္စကို `remote` ကို အသိပေးဖို့ လိုအုံးမှာဆိုတော့ အပေါ်မှာရေးထားတဲ့ [branch ကို remote ဆီတွန်းတဲ့](D#changing-a-branch-name11) command တွေနဲ့ ပြန်တွန်းဖို့ လိုကောင်းလိုပါမယ်။</em>

### Deleting Commit(s)[^13]
`iss9` branch မှာ ရှိနေတဲ့ နောက်ဆုံး commit ၂ ခုကို ဖျက်ချင်ပြီ ဆိုပါစို့ 

        $ git checkout iss9
        $ git log
        $ git reset --hard <hash-of-second-last-commit>

`git reset --hard` က very dangerous command ပါ။  ဒါကြောင့် commit တွေကို hard reset လုပ်ပစ်မယ့်အစား branch အသစ်ပွားယူလိုက်တာ ပိုပြီး ကောင်းပါတယ်။ 

#### Creating a branch from a specific commit        

        $ git log --oneline // to find the commit hash
        $ git checkout -b <branch-name> <commit#>
        $ git log --online // to verify

# Remote Branch[^14]
Full list of remote references ကို ဒါတွေနဲ့ ကြည့်ပါ

        $ git ls-remote <remote>
---
        $ git remote show <remote>

ကောင်းတာက remote-tracking branch တွေရဲ့ အကူညီကို ယူတာပါ။

Remote-tracking branch(တွေ)ဟာ - 
- remote branch(တွေ) ရဲ့ <strong>state</strong> ကို ပြတဲ့ <strong>reference</strong> တွေပါ။[^15]
- <strong>local reference</strong>(တွေ) ဖြစ်ပြီး ကိုယ်ကသွား ရွေ့ပေးလို့ မရပါဘူး​။ Remote repository ရဲ့ state ကို တိတိကျကျ represent လုပ်နေသာ သေချာအောင် ၊ ကိုယ့်ဖက်က network communication တစ်ခုခုလုပ်လိုက်မှသာ Git က ရွေ့ပေးမှာဖြစ်ပါတယ်။  
- ကိုယ်နောက်ဆုံးအချိန် connect လုပ်ခဲ့တုန်းက remote repositories တွေထဲက ဘယ် branch တွေက ဘယ်နေရာမှာ ရှိနေတယ်ဆိုတာ သတိပေးမယ့် bookmark တွေဖြစ်ပါတယ်။

Remote-tracking branch တွေဟာ `<remote>/<branch>` form ကို ယူပါတယ်။ 




[^1]: ဒီ cheat sheet ထဲက command အများစုက (Pro Git - 2nd Edition - by Scott Chacon and Ben Straub)[https://git-scm.com/book/en/v2] ထဲကဖြစ်ပါတယ်။
[^2]: page 52
[^3]: page 92
[^4]: page 55
[^5]: page 65
[^6]: page 70
[^7]: page 73
[^8]: page 75
[^9]: page 76
[^10]: page 79
[^11]: page 81
[^12]: ChatGPT
[^13]: ChatGPT
[^14]: page 85
[^15]: page 86
