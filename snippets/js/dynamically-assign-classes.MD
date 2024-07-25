# Dynamically assign unique classes [^1]

JS ထဲမှာ `<div>` တွေ dynamically create လုပ်ပြီး တစ်ခုနဲ့ တစ်ခု မတူတဲ့ class တွေ assign လုပ်ချင်တဲ့အခါ အသုံးတည့်ပါတယ်။ [^2]

    const tempAnswersArray = ["aaaaa", "bbbbb", "ccccc", "ddddd"]; 
    // Example answers array
    
    const classList = ["ans-a", "ans-b", "ans-c", "ans-d"]; 
    // Array of classes
    
    const answersContainer = document.getElementById("section-answers"); 

    tempAnswersArray.forEach((answer, index) => {
      const tempAnswerContainer = document.createElement("div");
      tempAnswerContainer.classList.add("answer-container", classList[index]);

      ...

    });

[^1]: ဒီ code ကို chatGPT နဲ့ တူတူ ရေးထားတာဖြစ်ပါတယ်။
[^2]: IIG Myanmar ကျောင်း ရဲ့ 'Interactive Quiz #1' မှာ ဒီ code ကိုသုံးထားပါတယ်။  