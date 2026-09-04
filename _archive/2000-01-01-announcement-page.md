---
title: Announcement
author: RepoXu
math: true
mermaid: true
---

---

before you publish this page 2 the net, there are a few things you need to do

1. create a `_config.yml` file, which contains:

```yml
theme: jekyll-theme-modernist
```

2. rename current file (whatever it named) to `index.md`

3. find the website of jekyll and follow its instructions to deploy the page


---


## 来瞅一眼！！！

这是俺的 announcement 页面。

`现在啥也没有`

> 没有你还瞅啥
>
> 你瞅 nm 呢

我就试试这玩意支持不支持 md 语法

### 还搁这看呢？

真没啥好看的了，我刚看完数学题

就 tm 一个数学题，**烦**死我了，<u>根本算不出来</u> $$ x $$ 是多少

$$ x^2 + \sin x = 0 $$

这玩意*咋算你说说*，这不**离大谱**么

### 你还看你还看，有啥好看的

我还能给你变出来个鸡蛋不成）

翻出来当年写的代码瞅瞅

```c++
// lambda0.cpp -- using lambda expressions
#include <iostream>
#include <vector>
#include <algorithm>
#include <cmath>
#include <ctime>
const long Size1 = 39L;
const long Size2 = 100*Size1;
const long Size3 = 100*Size2;

bool f3(int x) {return x % 3 == 0;}
bool f13(int x) {return x % 13 == 0;}

int main()
{
    using std::cout;
    std::vector<int> numbers(Size1);

    std::srand(std::time(0));
    std::generate(numbers.begin(), numbers.end(), std::rand);

// using function pointers
    cout << "Sample size = " << Size1 << '\n';

    int count3 = std::count_if(numbers.begin(), numbers.end(), f3);
    cout << "Count of numbers divisible by 3: " << count3 << '\n';
    int count13 = std::count_if(numbers.begin(), numbers.end(), f13);
    cout << "Count of numbers divisible by 13: " << count13 << "\n\n";

// increase number of numbers
    numbers.resize(Size2);
    std::generate(numbers.begin(), numbers.end(), std::rand);
    cout << "Sample size = " << Size2 << '\n';
// using a functor
    class f_mod
    {
    private:
        int dv;
    public:
        f_mod(int d = 1) : dv(d) {}
        bool operator()(int x) {return x % dv == 0;}
    };

    count3 = std::count_if(numbers.begin(), numbers.end(), f_mod(3));
    cout << "Count of numbers divisible by 3: " << count3 << '\n';
    count13 = std::count_if(numbers.begin(), numbers.end(), f_mod(13));
    cout << "Count of numbers divisible by 13: " << count13 << "\n\n";

// increase number of numbers again
    numbers.resize(Size3);
    std::generate(numbers.begin(), numbers.end(), std::rand);
    cout << "Sample size = " << Size3 << '\n';
// using lambdas
    count3 = std::count_if(numbers.begin(), numbers.end(),
             [](int x){return x % 3 == 0;});
    cout << "Count of numbers divisible by 3: " << count3 << '\n';
    count13 = std::count_if(numbers.begin(), numbers.end(),
              [](int x){return x % 13 == 0;});
    cout << "Count of numbers divisible by 13: " << count13 << '\n';

    // std::cin.get();
    return 0;
}
```

有啥好看的真是

这我从那本<u>《C++ Primer Plus》</u>上**第18章**摘出来的代码，文件是叫 `lambda0.cpp` 。

### 有什么好看的真是....

我给你放个美女图行不）

![the queen](https://cdn.akamai.steamstatic.com/steam/apps/1580050/ss_a7a0a8ee0861b02cd6d6fa7721a5ee3fe3a386e5.jpg)

就问你：美不美？

死亡细胞里边儿滴！22年Q1季度马上要出滴新 DLC！叫什么“ **the Queen and the Sea** ”，霸气侧漏的女王！

<div style="color:blueviolet">
	<b>なんてハンサム！！！！</b>
</div>

#### 笑死

1. 别往下看啦....
   + 没意思哒...
2. 焯！

+ 有病病是不是！！！！

我看看还差啥没试过...

哦，表格格

什么？

哦

|    因素    |                         原因                         |
| :--------: | :--------------------------------------------------: |
|    粒度    |                    矿石颗粒的粗细                    |
| 矿浆液固比 |                接触面积，保证反应进行                |
|    酸度    |             影响 $$ UO_2^{2+} $$ 的生成              |
|   氧化剂   | 将矿石中的 $$ UO_2(IV) $$ 氧化至 $$ UO_2^{2+}(VI) $$ |
|    温度    |                       加速反应                       |
|    时间    |                      增加浸出率                      |

md 懒得改了

就这吧，

---

<div style="color:pink"> seyane ~ </div>
