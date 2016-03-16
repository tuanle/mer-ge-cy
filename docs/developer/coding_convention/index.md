Coding convention (Đối với dự án PHP, sử dụng framework CakePHP)

## Mục đích

Coding convention hay coding standard là một tập hợp các quy ước, cách thức viết, trình bày code nhằm các mục đích sau đây:

- Hỗ trợ người viết code trình bày ý tưởng rõ ràng, trong sáng, tránh các lỗi thường gặp về tên gọi, cú pháp, cấu trúc
- Hỗ trợ người viết code trong quá trình self-refactor
- Hỗ trợ đọc hiểu code trong quá trình maintain code của người khác

Vì vậy, vấn đề quan trọng nhất của coding convention là "hỗ trợ" chứ ko phải là "quy định". Bạn cần thực hành các thói quen sau:

- "Tuân thủ" các convention có tính hệ thống (cấu trúc thư mục, file, đặt tên class, hàm, biến,...) vì đây là các quy ước mang tính "nhận dạng". Người khác sẽ dựa vào những điểm này để đọc hiểu code của bạn, dó đó cần phải tuân thủ nghiêm ngặt.
- "Nên" làm theo các convention mang tính "tránh lỗi"

        Ví dụ lệnh so sánh nên đặt hằng số trước biến: 3 == $a, CONSTANT_PI == $b để lỡ có viết thành dấu "=" thì hệ thống sẽ báo lỗi cú pháp.

- "Tùy biến" các coding convention mang tính "visibility" tức là dễ nhìn, dễ đọc.

        // Ví dụ lệnh
        switch () {
            case 1:
            break; // Nên viết break thẳng hàng với case để giống như cấu trúc đóng mở block { ... }
        }

- Viết code nên theo thói quen cá nhân, quan trọng là bạn tự thấy dễ đọc dễ hiểu. Vì vậy không nên tránh các cách thể hiện đặc biệt miễn là cách thể hiện đó phải có một hiệu quả hay hiệu ứng nhất định nào đó.

## Giới thiệu chung

- Về coding convention, hiện tại đang có một số hệ thống thường được sử dụng như PSR, PEAR, Symfony, Zend,... Tuy nhiên các bản [PHP Specification Request (PSR)](http://www.php-fig.org/psr/) của nhóm [PHP Framework Interop Group (PHP FIG)](http://www.php-fig.org/) là được sử dụng phổ biến nhất.

*Hệ thống convention mang tính kế thừa, nghĩa là các quy ước không được quy định trong version này thì sẽ tuân theo version trước, ngược lại các quy ước được quy định ở version mới hơn sẽ được sử dụng thay cho version cũ. Điều này cũng đúng cho việc sử dụng framework. Nghĩa là các quy ước của riêng của framework sẽ có tính ưu tiên sử dụng cao hơn các quy ước chung của ngôn ngữ. Ngoài ra, cần tuân thủ theo convention tùy theo từng dự án đặc thù.*
