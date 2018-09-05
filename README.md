# Javascript: Execution Context là gì? Call Stack là gì?

 **Execution Context in Javascript** là gì?

Tôi cá là bạn không biết câu trả lời

Các thành phần cơ bản nhất của một ngôn ngữ lập trình là gì?

Các biến và hàm phải không? Mọi người đều có thể học những điều này.

Nhưng những gì nằm ngoài những điều cơ bản?

Những **pillars of Javascript** mà bạn nên làm chủ trước khi xem mình là một developer javascript trung cấp (hoặc thậm chí cao cấp)?

Có rất nhiều thứ như là: Scope, Closure, Callbacks, Prototype,..

BNhưng trước khi đi sâu hơn vào những khái niệm này, ít nhất bạn nên hiểu
**engine Javascript hoạt động như thế nào**.

Trong bài này, chúng tôi sẽ giới thiệu hai phần cơ bản của mọi Javascript
engine: **the Execution Context and the Call Stack**.

(Đừng sợ. Nó dễ hơn bạn nghĩ).

Sẵn sàng chưa?

Tài liệu này là một phần của [Advanced Javascript class available both as
remote 1 to 1 training](https://www.valentinog.com/) or as [on site training
in Europe](https://www.servermanaged.it/formazione-javascript-react.html).

## Javascript: Execution Context là gì ? Bạn sẽ học những gì?

Trong bài này bạn sẽ học:

  *  Javascript Engine hoạt động như thế nào
  *  Execution Context trong Javascript
  * Call Stack là gì
  * SỰ khác biệt giữa Global Execution Context và Local Execution Context

## Javascript: Execution Context là gì ? Javascript chạy Code của bạn như thế nào?

Javascript chạy code của bạn như thế nào?

Nếu bạn là một senior developer thì bạn có  thể đã biết câu trả lời

Nếu bạn là người mới bắt đầu, chúng tôi sẽ cùng nhau tìm hiểu.

Sự thật là, bên trong Javascript không hề đơn giản.

Nhưng tôi đảm bảo bạn có thể học chúng

Và vào thời điểm bạn học chúng, bạn sẽ cảm thấy được trao quyền và thông minh hơn.

Bằng cách xem xét chức năng bên trong Javascript, bạn sẽ trở thành một Javascript developer tốt hơn, ngay cả khi bạn không thể nắm vững từng chi tiết.

Bây giờ, hãy xem đoạn code sau:

    
    
    var num = 2; function pow(num) { return num * num;
    }
    

Đã xong?

Nó trông không khó!

Bây giờ hãy cho tôi biết: **bạn nghĩ trình duyệt sẽ thực hiện đoạn code đó theo thứ tự nào**?

Nói cách khác, nếu bạn là trình duyệt, bạn sẽ đọc đoạn code đó như thế nào?

Nghe có vẻ dễ dàng

Hầu hết mọi người nghĩ rằng "yeah, trình duyệt thực thi hàm pow và trả về kết quả, sau đó nó gán 2 vào num."

Bạn có muốn biết câu trả lời của học sinh của tôi không?

_Từ trên xuống dưới_

_Trình duyệt sẽ bắt đầu ở hàm pow, thực hiện tính num * num_

_JS engine sẽ chạy từng dòng_ (kiểu như vậy)

Tôi đã mong chờ điều đó

Tôi đã nói chính xác những điều này nhiều năm trước.

Trong phần tiếp theo, bạn sẽ khám phá machinery đằng sau **những dòng code đơn giản đó*.

## Javascript: The Execution Context là gì? Javascript Engines

Bạn có muốn trở thành Javascript developer mức trung bình không?

Tôi cá là bạn sẽ không.

Nếu bạn muốn tạo ấn tượng tốt trong một cuộc phỏng vấn về Javascript, ít nhất bạn nên biết **cách Javascript chạy code của bạn**

(Và một loạt các thứ khác nữa nhưng tôi sẽ không nêu ra ở đây).

Đừng vội vàng dựa trên những khái niệm này.

Bạn không thể học mọi thứ trong một ngày. Nó sẽ tốn thời gian

Tin tốt? Tôi sẽ làm cho mọi thứ dễ hiểu đối với mọi người (ít nhất tôi sẽ thử).

Để hiểu cách Javascript chạy code của bạn, chúng ta phải đáp ứng điều đáng sợ đầu tiên: **the Execution Context**.

 Execution Context trong Javascript là gì?

**Mỗi khi bạn chạy Javascript trong trình duyệt** (hoặc trên Node) **engine sẽ đi qua một loạt các bước.**.

Một trong những bước này liên quan đến việc **tạo ra Global Execution Context**.

Nhưng chờ đã, **engine là gì**?

Đó, Javascript engine là một "công cụ" để chạy code Javascript.

Hiện nay có 2 Javascript engine nổi bật là **Google V8** và
**SpiderMonkey**.

V8 là JavaScript engine mã nguồn mở của Google, được sử dụng trong Google Chrome và 122 Node.js.

SpiderMonkey là JavaScript engine của Mozilla, được sử dụng trong Firefox.

So far we have the Javascript engine and an Execution Context.

Now it's time to understand how they work together.

## Javascript: What Is The Execution Context? How It Works?

**The engine creates a Global Execution Context** every time you run some Javascript code.

Execution Context is a fancy word for describing the environment in which your
Javascript code runs.

It's hard to visualize these abstract things, I feel you.

For now think of the Global Execution Context as a box:

[![Global Execution
Context](https://res.cloudinary.com/practicaldev/image/fetch/s--jWWiNqCD--/c_l
imit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://thepracticaldev.s3.ama
zonaws.com/i/ptgf765a4989zd6twwfp.png)](https://res.cloudinary.com/practicalde
v/image/fetch/s--jWWiNqCD--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880
/https://thepracticaldev.s3.amazonaws.com/i/ptgf765a4989zd6twwfp.png)

Let's look again at our code:

    
    
    var num = 2; function pow(num) { return num * num;
    }
    

How does the engine read that code?

Here is a simplified version:

_**Engine**: Line one. There's a variable! Cool. Let's store it in the Global
Memory._

_**Engine**: Line three. I see a function declaration. Cool. Let's store that
in the Global Memory too!_

_**Engine**: Looks like I'm done._

If I were to ask you again: how does the browser "see" the following code,
what would you say?

Yeah, it's kind of top to bottom but ...

As you can see the engine does not run the function pow!

It's a **function declaration**, not a function call.

The above code will translate in some values stored in the **Global Memory**:
a function declaration and a variable.

**Global Memory**?

Valentino, I'm already confused by the Execution Context and now you're
throwing the Global Memory at me?

Yes I am.

Let's see what the Global Memory is.

## Javascript: What Is The Execution Context? The Global Memory

The **Javascript engine has a Global Memory too**.

The Global Memory contains global variables and function declarations for
later use.

If you read "Scope and Closures" by Kyle Simpson you may find that the Global
Memory overlaps with the concept of Global Scope.

In fact they are the same thing.

I'm flying 10,000 feet high here, for a good reason.

Those are hard concepts.

But you shouldn't worry for now.

I want you to understand two important pieces of our puzzle.

When the Javascript engine runs your code it creates:

  * a Global Execution context
  * a Global Memory (also called Global Scope or Global Variable Environment)

Is everything clear?

If I were you at this point I'll:

  * write down some Javascript code
  * parse the code step by step as you were the engine
  * make a graphic representation of both the Global Execution context and the Global Memory during the execution

You can write the exercise on paper or with a prototyping tool.

For my tiny example the picture will look like so:

[![A graphic representation of Javascript Execution Context / Global
Memory](https://res.cloudinary.com/practicaldev/image/fetch/s--Ae3LEIz8--/c_li
mit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://thepracticaldev.s3.amaz
onaws.com/i/7sreqswm895lrphw4xy2.png)](https://res.cloudinary.com/practicaldev
/image/fetch/s--Ae3LEIz8--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/
https://thepracticaldev.s3.amazonaws.com/i/7sreqswm895lrphw4xy2.png)

In the next section we'll look at another scary thing: the **Call Stack**.

Do you have a clear picture of **how** the **Execution Context**, the **Global
Memory** and the **Javascript engine fits together**?

If not take your time to review the previous section.

We're going to introduce another piece in our puzzle: the **Call Stack**.

Let's see what happens during code execution.

Let's first recap what happens when the Javascript engin runs your code.

It creates:

  * a Global Execution context
  * a Global Memory

Besides that in our example nothing more happened:

    
    
    var num = 2; function pow(num) { return num * num;
    }
    

The code is a pure allocation of values.

Let's take a step further.

What happens if I call the function?

    
    
    var num = 2; function pow(num) { return num * num;
    } var res = pow(num);
    

Interesting question.

The act of **calling a function in Javascript makes the engine ask for help**.

And that help comes from a friend of the Javascript engine: the **Call
Stack**.

It might not sound obvious but the **Javascript engine needs to keep track of
what's happening**.

It relies on the Call Stack for that.

What is the Call Stack in Javascript?

The **Call Stack is like a log of the current execution of the program**.

In reality it's a data structure: [a
stack](https://en.wikipedia.org/wiki/Stack_\(abstract_data_type\)).

How does exactly the Call Stack work?

Unsurprisingly it has two methods: **push** and **pop**.

**Pushing** is the act of **putting something into the stack**.

That is, **when you run a function in Javascript, the engine pushes that
function into the Call Stack**.

Every function call gets pushed into the Call Stack.

The **first thing that gets pushed is main()** (or global()), the main thread
of execution of your Javascript program.

Now, the previous picture will look like so:

[![Javascript Call
Stack](https://res.cloudinary.com/practicaldev/image/fetch/s--u-ktmKSh--/c_lim
it%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://thepracticaldev.s3.amazo
naws.com/i/ww11po2kybdij4zino4r.png)](https://res.cloudinary.com/practicaldev/
image/fetch/s--u-ktmKSh--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/h
ttps://thepracticaldev.s3.amazonaws.com/i/ww11po2kybdij4zino4r.png)

**Popping** on the other end is the act of **removing something from the stack**.

When a function ends executing it gets popped from the Call Stack.

And our Call Stack will look like the following:

[![Javascript Call Stack
Pop](https://res.cloudinary.com/practicaldev/image/fetch/s--XzP4eR0c--/c_limit
%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://thepracticaldev.s3.amazona
ws.com/i/2zbqkyan7uu67xrhpx1b.png)](https://res.cloudinary.com/practicaldev/im
age/fetch/s--XzP4eR0c--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/htt
ps://thepracticaldev.s3.amazonaws.com/i/2zbqkyan7uu67xrhpx1b.png)

And now you're ready to master every Javascript concept out there.

But where not done! Go to the next section!

## Advanced Javascript: What Is The Execution Context? The Local Execution
Context

Everything seems clear so far.

Are we missing something?

We know that the **Javascript engine creates a Global Execution context and a
Global Memory**.

Then, when you call a function in your code:

  * the Javascript engine asks for help
  * that help comes from a friend of the Javascript engine: the **Call Stack**
  * the **Call Stack keep tracks of what function is being called** in your code

Yet **another thing has to happen when you run a function** in Javascript.

First, **the function appears in the Global Execution context**.

Then, **another mini-context appears alongside the function**.

That little new box is called **Local Execution Context**.

A Local Execution context gets created inside that function!

What??

If you noticed, in the previous picture a new variable appears in the Global
memory: **var _res_**.

The variables **_res_** has a value of **undefined at first**.

Then as soon as **pow** appears in the **Global Execution Context, the
function executes and _res_ takes its return value**.

During the execution phase a Local Execution Context gets created, alongside a
Local Memory for holding up local variables.

What a powerful concept.

[![Local Execution
Context](https://res.cloudinary.com/practicaldev/image/fetch/s--Zpkb7RDS--/c_l
imit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://thepracticaldev.s3.ama
zonaws.com/i/8qoepadnbmo8alj8h0vi.png)](https://res.cloudinary.com/practicalde
v/image/fetch/s--Zpkb7RDS--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880
/https://thepracticaldev.s3.amazonaws.com/i/8qoepadnbmo8alj8h0vi.png)

Keep that in mind.

Understanding both the **Global and the Local Execution Context is the key for
mastering Scope and Closures**.

## Javascript: What Is The Execution Context? What Is The Call Stack? Wrapping
up

Can you believe what's behind 4 lines of code?

The Javascript engine creates an **Execution Context, a Global Memory, and a
Call Stack**.

But once you call a function the engine creates a **Local Execution Context
which has a Local Memory**.

By the end of this post you should be able to understand what happens when you
run some Javascript code.

Often overlooked, Javascript internals are always seen as misterious things by
new developers.

Yet they are the **key for mastering advanced Javascript concepts**.

If you learn Execution Context, Global Memory, and the Call Stack, **then
Scope, Closures, Callbacks and other stuff will be easy as a breeze**.

In particular, understanding the Call Stack is paramount.

All the Javascript will start to make sense once you visualize it: you will
finally understand **why Javascript is asynchronous** and why we do need
Callbacks.

Did you know **what's behind 4 lines of Javascript code**?

Now you know.

Thanks for reading!

This material is part of my [Advanced Javascript class available both as
remote 1 to 1 training](https://www.valentinog.com/) or as [on site training
in Europe](https://www.servermanaged.it/formazione-javascript-react.html).
