# Merging Objects[^1]
    function merge(target, ...sources) {
    for (let source of sources) { // source object တစ်ခုမက ရှိနေခဲ့သော်
        for (let key of Object.keys(source)) {
            if (!(key in target)) {
                target[key] = source[key];
            }
        }
    }
    return target;
}

---
    let target = {
        a: 100,
        b: 200,
        y: 5900,
        z: 6000,
    }

    let source1 = {
        a: 300,
        b: 400,
        c: 300,
        d: 400,
    }

    let source2 = {
        a: 0,
        e: 500,
        f: 600,
        z: 10000,
    }

---
`Object.assign` သုံးမယ်ဆိုရင် -

    Object.assign(target, source1, source2);

source ရဲ့ property က target မှာလဲ ရှိနေရင် overwrite လုပ်ပြီး မရှိသေးတဲ့ property တွေကိုပဲ ထပ်ပေါင်းတာမို့ result က ဒီလိုဖြစ်သွားပါမယ်။

    > target

    <- {a: 0, b: 400, y: 5900, z: 10000, c: 300, …}
        a: 0
        b: 400
        c: 300
        d: 400
        e: 500
        f: 600
        y: 5900
        z: 10000
        [[Prototype]]: Object

အဲ့လိုမဖြစ်ချင်ပဲ target မှာမရှိသေးတဲ့ property တွေကိုပဲ source တွေဆီက ယူပြီး merge လုပ်မယ်ဆိုရင်- 
    
    merge(target, source1, source2)

result က ဒီလိုဖြစ်မှာပါ။

    > target

    <- {a: 100, b: 200, y: 5900, z: 6000, c: 300, …}
        a: 100
        b: 200
        c: 300
        d: 400
        e: 500
        f: 600
        y: 5900
        z: 6000
        [[Prototype]]: Object

[^1]: [JavaScript: The Definitive Guide, 7th Edition by David Flanagan](https://www.oreilly.com/library/view/javascript-the-definitive/9781491952016/) - page 143 မှာတဲ့ code snippet ပါ။ 