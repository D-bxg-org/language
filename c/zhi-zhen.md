# 指针

想了很多种解释方法，不如我直接把指针的规定写法展示给你。

`int *a` 

可能很多人接触的指针定义是这个样子的，我们先不讨论它，我们再看一种样式

`int* a` 

此种定义和上面的定义有区别吗？没有。这个地方没什么可解释的，这是一种规定，C语言规定了这么写就是定义指针变量。

`int * a` 

还有这种写法，也是定义一个指针变量，没什么原因，这就是种规定。

**C语言规定了，上面三种写法都是定义一个指针变量。怎么写都不错。**

当然，我到现在也没解释指针，你的那些疑问我也都还没解答，不要着急，我们一步步来，你现在至少学会了怎么定义一个指针变量，不是吗？

我一直认为，指针不好理解，是因为大部分同学在学习指针时，依旧是以学习之前的一些规定的思维去理解，什么“定义变量就是在内存里开辟一块空间来存放值”，又是“for循环有三个要素”，更甚者连上两个定义还没太明白，于是带着“指针不好理解”这种人云亦云的想法开始了指针学习。

现在我希望你放空之前对指针的理解，我来带着你真正的梳理一遍指针。同时在梳理完后，逐一回答你的那些对指针的疑问。

我们上面已经讲到了，指针的定义，我现在希望你，无论看到上面哪三种定义，都自动转化成第二种，也就是`int* a` 这一种。这种定义更符合指针变量在我们思维理解中指针应该是什么东西。

当然，我知道其实第一种写的更多，或者你的老师，你看到的一些程序，都是第一种写法，没关系，你理解的时候，按照第二种方式去理解就好，因为我们刚刚说过，怎么定义都没错，**你理解的时候按照第二种理解就好。**

我们先不着急讲什么指针的定义初始化、指向指针的指针这些既没意思，又复杂的定义。我们先好好的看看，究竟，我们定义了一个指针变量，这个变量，它究竟做了什么，有什么用，它到底是怎么一回事。

如果你看过我讲的“数据类型”，应该很明了，数据类型其实是规定了一块内存，在输出和输入时，应该怎么对待内存里的数据。同时我也讲到了，C不会判断输入这块内存的数据是不是符合这个内存的数据类型的定义，C只在你输出时看看，你这个数据是不是这个数据类型的，不是C就要告诉你：“你放的不对，你把这个数据取出来用的时候可能会有问题，需要你更改数据类型，或者把这个内存里的数据存对”。

那么指针变量干了什么呢？同学你注意到，我们称呼指针变量的时候，是在变量前加了个“指针”进行修饰，但它的本质也是变量，是变量，它就应该需要一块内存来存放东西，那它存的是什么呢？

地址！

你可能会快速的告诉我，存的是地址，的确，它存的是地址，但指针变量表示的，不仅仅是它存放了一个地址。让我详细的跟你讲讲：

`int* a` 

我们还是以这个举例，我们说，这个变量存放了地址，那我要问，是谁存放了地址？你可能听不明白我的问题，我来具体些问，是`* a` 存放了地址，还是`int* a` 存放了地址，还是`a` 存放了地址？

你可能不太知道了，有些支支吾吾，这没关系，书上写的定义是十分不具体的，是不符合人学习过程的，它只说了结果，人不会看到答案想到推导流程中的细节理解的。

其实是`a` 存放了地址。你现在可能已经开始有些疑惑了，没关系，你现在脑子里只需要记得两个概念：一是：我们定义指针变量，要这样写`int* a` ；二是：指针变量定义好后，`a` 里存放的是地址。

你可能会有这么一个疑问，到底我们说的指针变量是指谁？先不必着急，你脑子里先有上面两个概念，剩下的事情就非常好办了。

我来继续讲些规定，并把这些规定用我们好理解的方式解释一下。这个时候我们不得不写些无意义的代码来举举例子：

```c
int a = 0;
int* b;
int c;
c = &a;
b = c;
b = &a;
```

你可以看到，我写了5行代码，都非常简单，我们挑你感兴趣的解释，第2行就是我们刚刚说的，定义了一个指针变量，第4行做的事情是把a变量的地址取到，并地址这个值存到c变量中。第5行做了什么？是不是就是把c变量中存放着的a的地址存放到了b中？b是什么？是不是我们刚刚说的，指针变量存放地址的地方？那我在第6行写的是不是就是直接把a变量取到的地址存放到了b中？

好，我们再来讲个规定：

```c
int a = 123;
int* b;
b = &a;
printf(a); // 这个值是123
printf(*b); // 这个值也是123
```

什么意思？意思就是，如果我们在存放地址的`b` 前，加上一个`*` ，`*b` 就是变量`a` 。同学，注意我的措辞，`*b` 就是`a` 。就是说，`*b` 这个整体，得是`*` 加上`b` ，两个得合起来组成`*b` 才能代表变量`a` 。他俩不能分开，分开只有b你知道，就是个存了地址的东西，只有带上`*` 才能说，`*b` 是变量`a` 。

我们来具体的解释下：`b` 就是个存放地址的东西，但一旦`b` 前面带上了`*` ，它就是存放着的地址的那个变量了，是100%一样了。我们现在可以回答谁是指针变量了，`*b` 就是指针变量。

那么我们就有三个定义：

1. 定义指针变量写成`int* a` 
2. `a` 存放的是地址
3. `*a` 是指针变量，100%等价于把地址存放在`a` 里的那个变量。

这就是指针变量。你可能还有些震惊，这就是指针变量？对，这就是指针变量。你的那些疑问和指针变量没什么关系，和指针变量的使用有关系。我们现在来一个个回答你的问题，其实只需要回答几个，你的所有问题就都解决了。

```c
int fun(int* a)
{
    // ...
    return 0;
}
```

这个函数的形参取的是谁？是变量地址。回答完毕。为什么？我们刚刚就说到了，a里存的是什么？地址。也就是说，定义一个指针变量，用的数据类型，还额外声明了一下它是个指针变量。我们只要用`*` 这个符号，后面跟个写了地址的东西，就能操作那个地址的变量。

同时，我们应该注意到，a变量存放的变量地址，这个变量地址对应的变量的数据类型应该为int。

让我们来写点小例子

```c
int swap(int* pA, int* pB)

int main(){
    int a,b;
    a=1;
    b=2;
    
    printf("a = %d,b = %d\n",a,b);//会打印a = 1,b = 2
    swap(&a,&b);
    printf("a = %d,b = %d\n",a,b);//会打印a = 2,b = 1
    return 0;
}

int swap(int* pA, int* pB){
    int temp;
    
    temp = *pA ;
    *pA = *pB;
    *pB = temp;
}

```

```c
typedef struct LNode
{
    int data;
    struct LNode* next;
}LNode;
typedef LNode* LinkList;
LinkList a; // 100%等价于 LNode* a;

int InitList(LinkList* l)// 此处的LinkList* l <==> LNode* (* l)
{
    (*l) = (LinkList) malloc(sizeof(LNode));// 是(*l)存放头节点的地址，不是l。
                                            // 取变量应该写 *(* l).data
}
```

```c
#include <stdio.h>

int getA( int* a ){
    printf("%d", *a);
    return 0;
}

int newGetA(int &a){// c++写法
    printf("%d", a);
    return 0;
}

int main(){
    int a = 1;
    int* pa = &a;
    getA(&a);
    getA(pa);
    newGetA(a);// c++ 写法
    return 0;
}
```

