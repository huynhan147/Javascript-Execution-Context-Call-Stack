# Javascript: Execution Context là gì? Call Stack là gì?

 **Execution Context in Javascript** là gì?

Tôi cá là bạn không biết câu trả lời

Các thành phần cơ bản nhất của một ngôn ngữ lập trình là gì?

Các biến và hàm phải không? Mọi người đều có thể học những điều này.

Nhưng những gì nằm ngoài những điều cơ bản?

Những **trụ cột trong Javascript** mà bạn nên làm chủ trước khi xem mình là một developer javascript trung cấp (hoặc thậm chí cao cấp)?

Có rất nhiều thứ như là: Scope, Closure, Callbacks, Prototype,..

Nhưng trước khi đi sâu hơn vào những khái niệm này, ít nhất bạn nên hiểu **engine Javascript hoạt động như thế nào**.

Trong bài này, chúng tôi sẽ giới thiệu hai phần cơ bản của mọi Javascript engine: **the Execution Context và the Call Stack**.

(Đừng sợ. Nó dễ hơn bạn nghĩ nhiều).

Sẵn sàng chưa?

Tài liệu này là một phần của [Advanced Javascript class available both as
remote 1 to 1 training](https://www.valentinog.com/) hoặc trong cuốn [on site training
in Europe](https://www.servermanaged.it/formazione-javascript-react.html).

## Javascript: Execution Context là gì ? Bạn sẽ học những gì?

Trong bài này bạn sẽ học:

  * Javascript Engine hoạt động như thế nào
  * Execution Context trong Javascript
  * Call Stack là gì
  * SỰ khác biệt giữa Global Execution Context và Local Execution Context

## Javascript: Execution Context là gì ? Javascript chạy Code của bạn như thế nào?

Javascript chạy code của bạn như thế nào?

Nếu bạn là một senior developer thì bạn có  thể đã biết câu trả lời

Nếu bạn là người mới bắt đầu, chúng ta sẽ cùng nhau tìm hiểu.

Sự thật là, bên trong Javascript không hề đơn giản.

Nhưng tôi đảm bảo bạn có thể học chúng

Và vào thời điểm bạn học chúng, bạn sẽ cảm thấy đầy quyền lực và thông minh hơn.

Bằng cách xem xét chức năng bên trong Javascript, bạn sẽ trở thành một Javascript developer tốt hơn, ngay cả khi bạn không thể nắm vững từng chi tiết.

Bây giờ, hãy xem đoạn code sau:

    
 ```   
    var num = 2; 
    function pow(num) { return num * num;
    }
 ```  

Xong chưa?

Nó có vẻ không khó!

Bây giờ hãy cho tôi biết: **bạn nghĩ trình duyệt sẽ thực hiện đoạn code đó theo thứ tự nào**?

Nói cách khác, nếu bạn là trình duyệt, bạn sẽ đọc đoạn code đó như thế nào?

Nghe thì có vẻ dễ dàng

Hầu hết mọi người nghĩ rằng "yeah, trình duyệt thực thi hàm pow và trả về kết quả, sau đó nó gán 2 vào num."

Bạn có muốn biết các câu trả lời của học sinh của tôi không?

_Từ trên xuống dưới_

_Trình duyệt sẽ bắt đầu ở hàm pow, thực hiện tính num * num_

_JS engine sẽ chạy từng dòng_ (kiểu như vậy)

Tôi đã mong chờ điều đó

Tôi cũng đã nói những điều này nhiều năm trước.

Trong phần tiếp theo, bạn sẽ khám phá cơ chế đằng sau **những dòng code đơn giản đó*.

## Javascript: The Execution Context là gì? Javascript Engines

Bạn có muốn trở thành Javascript developer mức trung bình không?

Tôi cá là bạn sẽ không.

Nếu bạn muốn tạo ấn tượng tốt trong một cuộc phỏng vấn về Javascript, ít nhất bạn nên biết **cách Javascript thực hiện code của bạn**

(Và một loạt các thứ khác nữa nhưng tôi sẽ không nêu ra ở đây).

Đừng vội vàng lướt qua những khái niệm này.

Bạn không thể học mọi thứ trong một ngày. Nó sẽ tốn nhiều thời gian

Tin tốt? Tôi sẽ làm cho mọi thứ dễ hiểu đối với mọi người (ít nhất thì tôi sẽ cố).

Để hiểu cách Javascript chạy code của bạn, chúng ta phải tìm hiểu thứ đáng sợ đầu tiên: **the Execution Context**.

 Execution Context trong Javascript là gì?

**Mỗi khi bạn chạy Javascript trong trình duyệt** (hoặc trên NodeJS) **engine sẽ đi qua một loạt các bước.**.

Một trong những bước này liên quan đến việc **tạo ra Global Execution Context**.

Nhưng chờ đã, **engine là gì**?

Đó, Javascript engine là một "công cụ" để chạy code Javascript.

Hiện nay có 2 Javascript engine nổi bật là **Google V8** và **SpiderMonkey**.

V8 là JavaScript engine mã nguồn mở của Google, được sử dụng trong Google Chrome và Node.js.

SpiderMonkey là JavaScript engine của Mozilla, được sử dụng trong Firefox.

Tới đây chúng ta đã có Javascript engine và Execution Context.

Bây giờ là lúc để tìm hiểu xem chúng làm việc với nhau như thế nào.

## Javascript: The Execution Context là gì? Nó hoạt động như thế nào?

**Engine tạo ra một Global Execution Context** mỗi khi bạn chạy code Javascript.

Execution Context là một từ ưa thích để mô tả môi trường mà code Javascript của bạn chạy.

Tôi biết bạn sẽ khó hình dung những điều trừu tượng này

Bây giờ hãy nghĩ  Global Execution Context như là một cái hộp:

[![Global Execution
Context](https://res.cloudinary.com/practicaldev/image/fetch/s--jWWiNqCD--/c_l
imit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://thepracticaldev.s3.ama
zonaws.com/i/ptgf765a4989zd6twwfp.png)](https://res.cloudinary.com/practicalde
v/image/fetch/s--jWWiNqCD--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880
/https://thepracticaldev.s3.amazonaws.com/i/ptgf765a4989zd6twwfp.png)

Hãy xem lại code của chúng tôi:

    
    ```
    var num = 2; 
    function pow(num) { return num * num;
    }
    ```

Engine đọc code này như thế nào?

Đây là một câu trả lời đơn giản:

_**Engine**:  Dòng 1. Có một biến! Tuyệt. Hãy lưu trữ nó trong bộ Global Memory._

_**Engine**: Dòng 3. Tôi thấy một khai báo hàm. Tuyệt. Hãy lưu trữ nó trong Global Memory!_

_**Engine**: Có vẻ như tôi đã xong_

Nếu tôi hỏi lại bạn: trình duyệt "xem" đoạn code sau đây như thế nào, bạn sẽ nói gì?

Yeah, nó thuộc loại từ trên xuống nhưng .. .

Như bạn có thể thấy engine thực hiện hàm pow!

Đó là một **khai báo hàm**, chứ không phải một lời gọi hàm.

Đoạn mã trên sẽ dịch thành một số giá trị được lưu trong **Global Memory**: một khai báo hàm và một biến

**Global Memory**?

Valentino, Tôi đã đang nhầm lẫn về Execution Context và giờ bạn đang ném Global Memory vào tôi?

Vâng đúng vậy.

Hãy xem Global Memory là gì.

## Javascript: Execution Context là gì? The Global Memory

 **Javascript engine cũng có một Global Memory**.

Global Memory chứa các biến toàn cục và các khai báo hàm để sử dụng sau này.

Nếu bạn đọc "Scope and Closures" của Kyle Simpson, bạn có thể thấy rằng khái niệm của Global Memory trùng lặp với khái niệm Global Scope.

Trong thực tế, chúng thực sự giống nhau.

Vì một lý do chính đáng, tôi đang lơ lửng ở 10.000 feet ở đây.

Đó là những khái niệm khó.

Nhưng bây giờ bạn không nên lo lắng.

Tôi muốn bạn hiểu hai phần quan trọng trong câu đố của chúng tôi.

Khi công cụ Javascript chạy code của bạn, nó tạo ra:

  * một Global Execution context
  * một Global Memory (còn gọi là Global Scope hoặc Global Variable Environment)

Mọi thứ đã rõ ràng chưa?

Nếu tôi là bạn vào thời điểm này tôi sẽ:

  * Viết một vài đoạn code Javascript
  * Phân tích cú pháp của code từng bước một khi bạn là một engine
  * vẽ ra một đồ thị biểu diễn cả Global Execution Context và Global Memory trong suốt quá trình thực hiện.

Bạn có thể viết bài tập trên giấy hoặc bằng các công cụ tạo mẫu.

Đối với ví dụ nhỏ của tôi, hình ảnh sẽ như sau:

[![A graphic representation of Javascript Execution Context / Global
Memory](https://res.cloudinary.com/practicaldev/image/fetch/s--Ae3LEIz8--/c_li
mit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://thepracticaldev.s3.amaz
onaws.com/i/7sreqswm895lrphw4xy2.png)](https://res.cloudinary.com/practicaldev
/image/fetch/s--Ae3LEIz8--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/
https://thepracticaldev.s3.amazonaws.com/i/7sreqswm895lrphw4xy2.png)

Trong phần tiếp theo, chúng ta sẽ tìm hiểu một điều đáng sợ khác: **Call Stack**.

Bạn có một bức tranh rõ ràng về **Executation Context, Global Memory** và **Javascript engine** chúng có phù hợp với nhau hay không?

Nếu không thì hãy dành thời gian của bạn để xem lại phần trước.

Chúng tôi sẽ giới thiệu một phần khác trong câu đố của chúng tôi: **Call Stack**.

Hãy xem điều gì xảy ra trong quá trình thực thi code.

Trước tiên hãy tóm tắt lại những gì xảy ra khi Javascript engine chạy code của bạn.

Nó tạo ra:

  * một Global Execution context
  * một Global Memory

Bên cạnh đó trong ví dụ của chúng tôi không có gì xảy ra nữa:

    
    ```
    var num = 2; function pow(num) { return num * num;
    }
    ```
    

Đoạn code này là một phân bổ thuần túy các giá trị.

Hãy tiến thêm một bước nữa.

Điều gì xảy ra nếu tôi gọi hàm này?

    ```
    
    var num = 2; function pow(num) { return num * num;
    } var res = pow(num);
    ```

Đây là câu hỏi thú vị.

Hành động **gọi một hàm trong Javascript buộc engine phải yêu cầu được trợ giúp.**

Và sự trợ giúp đó đến từ một người bạn của Javascript engine: một **Call
Stack**.

Nó có thể không rõ ràng nhưng **Javascript engine cần phải theo dõi những gì đang xảy ra.**.

Nó dựa trên Call Stack để thực hiện điều đó.

Call Stack trong Javascript là gì?

**Call Stack giống như một bản ghi tiến trình hiện tại của chương trình**.

Trong thực tế nó là một cấu trúc dữ liệu: [một stack](https://en.wikipedia.org/wiki/Stack_\(abstract_data_type\)).

Chính xác thì Call Stack hoạt động như thế nào?

Không có gì đáng ngạc nhiên khi nó có hai method: **push** và **pop**.

**Pushing** là hành động **đưa một cái gì đó vào stack**.

Tức là, **khi bạn chạy một hàm trong Javascript, engine sẽ đẩy hàm đó vào trong Call Stack.**

Mọi lời gọi hàm đều được đẩy vào Call Stack.

**Điều đầu tiên được push là main()** (hoặc global()), luồng chính của việc thực thi chương trình Javascript của bạn.

Bây giờ, hình ảnh trước sẽ trông như sau:

[![Javascript Call
Stack](https://res.cloudinary.com/practicaldev/image/fetch/s--u-ktmKSh--/c_lim
it%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://thepracticaldev.s3.amazo
naws.com/i/ww11po2kybdij4zino4r.png)](https://res.cloudinary.com/practicaldev/
image/fetch/s--u-ktmKSh--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/h
ttps://thepracticaldev.s3.amazonaws.com/i/ww11po2kybdij4zino4r.png)

**Popping** ở đầu bên kia là hành động **xóa thứ gì đó khỏi stack**.

Khi một hàm kết thúc việc thực thi, nó sẽ được bỏ ra khỏi Call Stack

Và Call Stack của chúng ta sẽ trông giống như sau:

[![Javascript Call Stack
Pop](https://res.cloudinary.com/practicaldev/image/fetch/s--XzP4eR0c--/c_limit
%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://thepracticaldev.s3.amazona
ws.com/i/2zbqkyan7uu67xrhpx1b.png)](https://res.cloudinary.com/practicaldev/im
age/fetch/s--XzP4eR0c--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/htt
ps://thepracticaldev.s3.amazonaws.com/i/2zbqkyan7uu67xrhpx1b.png)

Và bây giờ bạn đã sẵn sàng để làm chủ mọi khái niệm của Javascript.

Nhưng ở đây chưa xong! Hãy chuyển đến phần tiếp theo!

## Advanced Javascript: The Execution Context là gì? The Local Execution Context

Mọi thứ dường như rõ ràng cho đến lúc này.

Chúng ta đang thiếu một cái gì đó?

Chúng ta biết rằng **Javascript engine tạo ra một Global Execution context và một
Global Memory**.

Sau đó, khi bạn gọi hàm trong code của bạn:

  * Javascript engine yêu cầu trợ giúp
  * sự trợ giúp đó đến từ một người bạn của công cụ Javascript: **Call Stack**
  * **Call Stack theo dõi các hàm đang được gọi** trong code của bạn

Tuy nhiên, **một điều khác đã xảy ra khi bạn chạy một hàm** trong Javascript.

Đầu tiên, **hàm xuất hiện trong Global Execution context**.

Tiếp theo, **một mini-context khác cũng xuất hiện cùng với hàm đó**

Cái hộp nhỏ mới này được gọi là **Local Execution Context**.

Một Local Execution context được tạo bên trong hàm đó!

What??

Nếu bạn nhận thấy, trong hình trước đó một biến mới xuất hiện trong Global memory: **var _res_**.

Các biến **_res_** có giá trị **ban đầu là undefined**.

Sau đó, ngay sau **pow** xuất hiện trong **Global Execution Context, hàm đó thực hiện, và _res_ lấy giá trị của nó để trả về.**.

Trong suốt giai đoạn thực thi, một Local Execution Context được tạo ra, cùng với một Local Memory để lưu các biến cục bộ.

Thật là một khái niệm mạnh mẽ.

[![Local Execution
Context](https://res.cloudinary.com/practicaldev/image/fetch/s--Zpkb7RDS--/c_l
imit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://thepracticaldev.s3.ama
zonaws.com/i/8qoepadnbmo8alj8h0vi.png)](https://res.cloudinary.com/practicalde
v/image/fetch/s--Zpkb7RDS--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880
/https://thepracticaldev.s3.amazonaws.com/i/8qoepadnbmo8alj8h0vi.png)

Hãy ghi nhớ nó.

Hiểu cả **Global và Local Execution Context là chìa khóa để làm chủ Scope và Closures.**

## Javascript: Execution Context là gì?  Call Stack là gì? Gói gọn lại

Bạn có thể tin những gì đằng sau 4 dòng code?

Javascript engine tạo ra **Execution Context, một Global Memory, và một
Call Stack**.

Nhưng một khi bạn gọi một hàm, engine sẽ tạo ra một **Local Execution Context
có một Local Memory**.

Đến cuối bài viết này, bạn sẽ có thể hiểu những gì sẽ xảy ra khi bạn chạy một đoạn code Javascript.

Thường bị bỏ qua, nội dung Javascript luôn được xem là những điều bí ẩn bởi các developer mới.

Tuy nhiên, chúng là **chìa khóa để làm chủ các khái niệm Javascript nâng cao**.

Nếu bạn hiểu về Execution Context, Global Memory, và Call Stack, **thì 
Scope, Closures, Callbacks và các nội dung khác sẽ dễ dàng hơn nhiều**.

Đặc biệt, sự hiểu biết Call Stack là cực kỳ quan trọng.

Tất cả các Javascript sẽ bắt đầu có ý nghĩa một khi bạn hình dung nó: cuối cùng bạn sẽ hiểu **tại sao Javascript là không đồng bộ** và tại sao chúng ta cần Callbacks.

Bạn có biết **những gì đằng sau 4 dòng code Javascript**?

Bây giờ bạn  đã biết

