BÀI TẬP AN TOÀN VÀ BẢO MẬT THÔNG TIN

Môn An toàn và bảo mật thông tin.

1\. tìm hiểu thuật toán mã hoá hiện đại DES, AES

&#x20;  mô tả đc thuật toán, quy trình mã hoá/giải mã

&#x20;  cài đặt AES trên 1 ngôn ngữ lập trình nào đó

2\. tìm hiểu về thuật toán mã hoá bất đối xứng RSA

&#x20;  nguyên lý sinh cặp khoá bí mật, công khai

3\. trình bày các mô hình hình áp dụng thuật toán RSA

&#x20;  xác thực người gửi, xác thực người nhận, cả 2

&#x20;  so sánh thời gian mã hoá/giải mã của RSA với AES.

&#x20;  đưa ra các dùng kết hợp sức mạnh của RSA và AES.



**1. TÌM HIỂU THUẬT TOÁN MÃ HÓA HIỆN ĐẠI DES VÀ AES**

*1.1. Mã hóa đối xứng*



Mã hóa đối xứng là phương pháp mã hóa trong đó người gửi và người nhận sử dụng cùng một khóa bí mật cho cả quá trình mã hóa và giải mã.



Quy trình:



Bản rõ

&#x20;  |

&#x20;  | Khóa bí mật

&#x20;  v

Mã hóa

&#x20;  |

&#x20;  v

Bản mã

&#x20;  |

&#x20;  | Khóa bí mật

&#x20;  v

Giải mã

&#x20;  |

&#x20;  v

Bản rõ



Ưu điểm của mã hóa đối xứng là tốc độ xử lý nhanh, phù hợp với việc mã hóa lượng dữ liệu lớn.



Nhược điểm là khóa bí mật phải được trao đổi giữa người gửi và người nhận một cách an toàn. Nếu khóa bị lộ, dữ liệu có thể bị giải mã.



Hai thuật toán mã hóa đối xứng tiêu biểu là DES và AES.



**1.2. Thuật toán DES**

*1.2.1. Khái niệm*



DES (Data Encryption Standard) là một thuật toán mã hóa đối xứng được phát triển để bảo vệ dữ liệu.



DES mã hóa dữ liệu theo từng khối có kích thước 64 bit. Khóa DES có độ dài 64 bit, trong đó 56 bit được sử dụng thực tế cho quá trình mã hóa và 8 bit còn lại được sử dụng cho mục đích kiểm tra.



DES sử dụng cấu trúc Feistel và thực hiện quá trình biến đổi dữ liệu qua 16 vòng mã hóa.



Hiện nay DES không còn được xem là an toàn cho các hệ thống hiện đại vì khóa thực tế chỉ có 56 bit, khiến việc thử toàn bộ không gian khóa bằng phương pháp vét cạn trở nên khả thi với năng lực tính toán hiện đại.



*1.2.2. Quy trình mã hóa DES*



Quá trình mã hóa DES gồm các bước chính:



Bước 1: Hoán vị ban đầu



Bản rõ 64 bit được đưa qua phép hoán vị ban đầu IP (Initial Permutation).



Sau đó dữ liệu được chia thành hai phần:



L0: 32 bit.

R0: 32 bit.

Bước 2: Thực hiện 16 vòng



Mỗi vòng sử dụng một khóa con khác nhau.



Công thức tổng quát:



Li = Ri-1



Ri = Li-1 XOR f(Ri-1, Ki)



Trong đó:



Li là nửa trái của dữ liệu tại vòng i.

Ri là nửa phải của dữ liệu tại vòng i.

Ki là khóa con của vòng i.

f là hàm biến đổi của DES.

Bước 3: Hoán vị cuối



Sau khi thực hiện 16 vòng, dữ liệu được đưa qua phép hoán vị cuối để tạo ra bản mã 64 bit.



*1.2.3. Quy trình giải mã DES*



Quá trình giải mã DES sử dụng cùng khóa bí mật với quá trình mã hóa.



Điểm khác biệt là các khóa con được sử dụng theo thứ tự ngược lại:



K16 → K15 → K14 → ... → K2 → K1



Sau khi thực hiện các vòng biến đổi và phép hoán vị cuối, bản mã được chuyển thành bản rõ ban đầu.



**1.3. Thuật toán AES**

*1.3.1. Khái niệm*



AES (Advanced Encryption Standard) là một thuật toán mã hóa đối xứng hiện đại được sử dụng rộng rãi trong các hệ thống bảo mật hiện nay.



AES mã hóa dữ liệu theo từng khối có kích thước cố định 128 bit.



AES hỗ trợ ba kích thước khóa:



Phiên bản	Độ dài khóa	Số vòng

AES-128	        128 bit	        10

AES-192	        192 bit	        12

AES-256	        256 bit	        14



AES có tốc độ xử lý nhanh, độ an toàn cao và phù hợp để mã hóa lượng dữ liệu lớn.



1.3.2. Cấu trúc AES



AES biểu diễn một khối dữ liệu 128 bit thành một ma trận gồm 4 hàng và 4 cột, mỗi phần tử là một byte.



Trong quá trình mã hóa, dữ liệu được biến đổi qua nhiều vòng. Mỗi vòng sử dụng một khóa con được tạo ra từ khóa ban đầu thông qua quá trình mở rộng khóa.



1.3.3. Quy trình mã hóa AES



Quá trình mã hóa AES gồm các bước chính:



Bước 1: AddRoundKey



Dữ liệu ban đầu được thực hiện phép XOR với khóa vòng đầu tiên.



State XOR RoundKey

Bước 2: SubBytes



Mỗi byte trong ma trận dữ liệu được thay thế bằng một byte khác thông qua bảng S-Box.



Mục đích của bước này là tạo ra sự biến đổi phi tuyến tính và tăng độ khó khi phân tích bản mã.



Bước 3: ShiftRows



Các hàng trong ma trận được dịch vòng với số lượng khác nhau:



Hàng thứ nhất: không dịch.

Hàng thứ hai: dịch 1 byte.

Hàng thứ ba: dịch 2 byte.

Hàng thứ tư: dịch 3 byte.



Bước này giúp dữ liệu được phân tán giữa các cột.



Bước 4: MixColumns



Các cột trong ma trận được biến đổi bằng các phép toán trong trường hữu hạn GF(2^8).



Mục đích là tăng khả năng khuếch tán dữ liệu.



Bước 5: AddRoundKey



Sau các phép biến đổi, dữ liệu tiếp tục được XOR với khóa vòng tương ứng.



Đối với AES-128, quá trình mã hóa gồm 10 vòng. Vòng cuối cùng không thực hiện bước MixColumns.



1.3.4. Quy trình giải mã AES



Quá trình giải mã AES thực hiện các phép biến đổi ngược với quá trình mã hóa.



Các phép biến đổi chính gồm:



\-InvShiftRows.

\-InvSubBytes.

\-AddRoundKey.

\-InvMixColumns.



Các khóa vòng được sử dụng theo thứ tự phù hợp để khôi phục dữ liệu ban đầu.



Sau khi hoàn thành quá trình giải mã, bản mã được chuyển trở lại thành bản rõ.



AES được sử dụng rộng rãi hơn DES do có kích thước khóa lớn hơn, mức độ bảo mật cao hơn và hiệu năng phù hợp với các hệ thống hiện đại.

!\[Cài đặt AES trên Python](01-cai-dat-aes.png)

Chú ý: cài đặt AES trên Python thành công

**2. TÌM HIỂU THUẬT TOÁN MÃ HÓA BẤT ĐỐI XỨNG RSA**

*2.1. Khái niệm mã hóa bất đối xứng*



Mã hóa bất đối xứng là phương pháp mã hóa sử dụng hai khóa khác nhau:



Khóa công khai (Public Key).

Khóa bí mật (Private Key).



Khóa công khai có thể được công khai cho mọi người biết, trong khi khóa bí mật phải được giữ an toàn.



Hai khóa có quan hệ toán học với nhau. Dữ liệu được mã hóa bằng một khóa có thể được giải mã bằng khóa tương ứng còn lại trong các phép sử dụng RSA phù hợp.



RSA là một trong những thuật toán mã hóa bất đối xứng nổi tiếng và được sử dụng trong trao đổi khóa, chữ ký số và các giao thức bảo mật.



*2.2. Nguyên lý sinh cặp khóa RSA*



Quá trình sinh cặp khóa RSA gồm các bước chính.



*Bước 1:* Chọn hai số nguyên tố



Chọn hai số nguyên tố lớn:



p

q



Trong hệ thống thực tế, hai số nguyên tố này phải đủ lớn để đảm bảo an toàn.



*Bước 2:* Tính n



Tính:



n = p × q



Giá trị n được sử dụng trong cả khóa công khai và khóa bí mật.



*Bước 3:* Tính hàm Euler



Tính:



φ(n) = (p - 1)(q - 1)

*Bước 4:* Chọn số mũ công khai e



Chọn một số nguyên e thỏa mãn:



1 < e < φ(n)



và:



gcd(e, φ(n)) = 1



Một giá trị thường được sử dụng trong RSA thực tế là:



e = 65537

*Bước 5:* Tính số mũ bí mật d



Tìm d sao cho:



d × e ≡ 1 (mod φ(n))



Nói cách khác, d là nghịch đảo modulo của e theo modulo φ(n).



*Bước 6:* Tạo cặp khóa



Khóa công khai:



Public Key = (e, n)



Khóa bí mật:



Private Key = (d, n)



Khóa bí mật phải được bảo vệ và không được cung cấp cho người khác.



*2.3. Quy trình mã hóa RSA*



Giả sử dữ liệu đã được biểu diễn thành một giá trị số m.



Người gửi sử dụng khóa công khai của người nhận:



(e, n)



để thực hiện mã hóa:



c = m^e mod n



Trong đó:



m là bản rõ.

e là số mũ công khai.

n là mô-đun RSA.

c là bản mã.



Sau khi mã hóa, bản mã có thể được truyền qua mạng.



*2.4. Quy trình giải mã RSA*



Người nhận sử dụng khóa bí mật:



(d, n)



để giải mã:



m = c^d mod n



Sau quá trình giải mã, người nhận thu được dữ liệu ban đầu.



Trong các hệ thống thực tế, RSA không thường được sử dụng trực tiếp để mã hóa dữ liệu lớn mà thường được dùng để bảo vệ khóa của thuật toán mã hóa đối xứng.



**3. CÁC MÔ HÌNH ÁP DỤNG THUẬT TOÁN RSA**

*3.1. Mô hình xác thực người gửi*



Trong mô hình xác thực người gửi, RSA được sử dụng để tạo và kiểm tra chữ ký số.



Người gửi sử dụng Private Key của mình để tạo chữ ký số cho dữ liệu.



Người nhận sử dụng Public Key của người gửi để kiểm tra chữ ký.



Quy trình:



Người gửi

&#x20;   |

&#x20;   | Dữ liệu

&#x20;   v

Tính giá trị băm

&#x20;   |

&#x20;   v

Tạo chữ ký bằng Private Key

&#x20;   |

&#x20;   v

Dữ liệu + Chữ ký

&#x20;   |

&#x20;   v

Người nhận

&#x20;   |

&#x20;   v

Kiểm tra chữ ký bằng Public Key



Mô hình này giúp người nhận xác định dữ liệu có được ký bằng khóa bí mật tương ứng hay không và phát hiện dữ liệu bị thay đổi.



*3.2. Mô hình xác thực người nhận*



Trong mô hình này, người gửi muốn đảm bảo rằng chỉ người nhận mới có thể giải mã dữ liệu.



Người gửi sử dụng Public Key của người nhận để mã hóa dữ liệu.



Người nhận sử dụng Private Key của mình để giải mã.



Quy trình:



Người gửi

&#x20;   |

&#x20;   | Dữ liệu

&#x20;   v

Public Key của người nhận

&#x20;   |

&#x20;   v

Mã hóa

&#x20;   |

&#x20;   v

Bản mã

&#x20;   |

&#x20;   v

Người nhận

&#x20;   |

&#x20;   | Private Key

&#x20;   v

Giải mã

&#x20;   |

&#x20;   v

Dữ liệu



Mô hình này cung cấp tính bí mật cho dữ liệu vì chỉ người sở hữu Private Key tương ứng mới có thể thực hiện quá trình giải mã phù hợp.



*3.3. Mô hình xác thực cả người gửi và người nhận*



Trong trường hợp cần đồng thời đảm bảo tính bí mật và xác thực, có thể kết hợp mã hóa và chữ ký số RSA.



Quy trình tổng quát:



Người gửi

&#x20;   |

&#x20;   | Dữ liệu

&#x20;   v

Tạo giá trị băm

&#x20;   |

&#x20;   v

Ký bằng Private Key người gửi

&#x20;   |

&#x20;   v

Chữ ký số

&#x20;   |

&#x20;   v

Mã hóa bằng Public Key người nhận

&#x20;   |

&#x20;   v

Truyền dữ liệu

&#x20;   |

&#x20;   v

Người nhận

&#x20;   |

&#x20;   v

Giải mã bằng Private Key

&#x20;   |

&#x20;   v

Dữ liệu + Chữ ký

&#x20;   |

&#x20;   v

Kiểm tra bằng Public Key người gửi



Mô hình này có thể cung cấp:



\-Tính bí mật.

\-Xác thực nguồn gửi.

\-Kiểm tra tính toàn vẹn của dữ liệu.

**4. SO SÁNH THỜI GIAN MÃ HÓA VÀ GIẢI MÃ RSA VỚI AES**



AES và RSA có đặc điểm hoạt động khác nhau nên thời gian xử lý cũng khác nhau.



*4.1. AES*



AES là thuật toán mã hóa đối xứng nên có tốc độ xử lý rất nhanh.



AES được thiết kế để mã hóa lượng dữ liệu lớn như:



\-Văn bản.

\-Hình ảnh.

\-Video.

\-File.

\-Dữ liệu cơ sở dữ liệu.

\-Dữ liệu truyền trên mạng.

*4.2. RSA*



RSA là thuật toán mã hóa bất đối xứng nên quá trình tính toán phức tạp hơn AES.



RSA thực hiện các phép tính trên các số nguyên lớn nên tốc độ mã hóa và giải mã thường chậm hơn AES rất nhiều.



RSA không phù hợp để mã hóa trực tiếp các file có kích thước lớn.



RSA thường được sử dụng cho:



\-Trao đổi khóa.

\-Chữ ký số.

\-Xác thực.

\-Mã hóa các dữ liệu nhỏ.

\-Bảo vệ khóa của thuật toán đối xứng.

*4.3. So sánh*

|Tiêu chí		|AES|RSA|
|-|-|-|
|Loại thuật toán|Đối xứng|Bất đối xứng|
|Số khóa|Một khóa bí mật|Khóa công khai và khóa bí mật|
|Tốc độ|Rất nhanh|Chậm hơn|
|Dữ liệu lớn<br />|Phù hợp|Không phù hợp|
|Trao đổi khóa|Khó khăn hơn|Phù hợp|
|Chữ ký số|Không phải chức năng chính|Phù hợp|
|Mục đích chính|Mã hóa dữ liệu|Trao đổi khóa và xác thực|





Nhìn chung, AES có tốc độ xử lý cao hơn RSA và phù hợp để mã hóa dữ liệu lớn. RSA có tốc độ chậm hơn nhưng có ưu điểm về quản lý khóa và xác thực.



Thời gian thực tế phụ thuộc vào kích thước dữ liệu, kích thước khóa, phần cứng và cách triển khai thuật toán.



**5. KẾT HỢP RSA VÀ AES**



Trong các hệ thống thực tế, RSA và AES thường được sử dụng kết hợp để tận dụng ưu điểm của cả hai thuật toán.



Mô hình này được gọi là mã hóa lai (Hybrid Encryption).



*5.1. Nguyên lý*



AES được sử dụng để mã hóa dữ liệu vì có tốc độ nhanh.



RSA được sử dụng để mã hóa và bảo vệ khóa AES.



Quy trình:



&#x20;                Người gửi

&#x20;                    |

&#x20;                    v

&#x20;             Tạo khóa AES

&#x20;                    |

&#x20;                    v

&#x20;            AES mã hóa dữ liệu

&#x20;                    |

&#x20;                    v

&#x20;             Dữ liệu mã hóa

&#x20;                    |

&#x20;                    |

&#x20;         RSA mã hóa khóa AES

&#x20;         bằng Public Key người nhận

&#x20;                    |

&#x20;                    v

&#x20;                  Gửi

&#x20;                    |

&#x20;                    v

&#x20;                Người nhận

&#x20;                    |

&#x20;                    v

&#x20;         RSA giải mã khóa AES

&#x20;         bằng Private Key

&#x20;                    |

&#x20;                    v

&#x20;                 AES Key

&#x20;                    |

&#x20;                    v

&#x20;            AES giải mã dữ liệu

&#x20;                    |

&#x20;                    v

&#x20;              Dữ liệu ban đầu

*5.2. Các bước thực hiện*

Bước 1



Người gửi tạo một khóa AES ngẫu nhiên.



Bước 2



Người gửi sử dụng AES để mã hóa dữ liệu cần truyền.



Bước 3



Người gửi sử dụng Public Key của người nhận để mã hóa khóa AES.



Bước 4



Người gửi gửi cho người nhận:



Dữ liệu đã mã hóa bằng AES + Khóa AES đã mã hóa bằng RSA

Bước 5



Người nhận sử dụng Private Key RSA để giải mã khóa AES.



Bước 6



Người nhận sử dụng khóa AES để giải mã dữ liệu.



**6. ƯU ĐIỂM CỦA VIỆC KẾT HỢP RSA VÀ AES**



Việc kết hợp hai thuật toán giúp tận dụng ưu điểm của từng loại.



\*AES

\-Tốc độ xử lý cao.

\-Phù hợp với dữ liệu lớn.

\-Hiệu quả khi mã hóa file và dữ liệu truyền tải.

\*RSA

\-Có thể sử dụng Public Key để bảo vệ khóa AES.

\-Không cần truyền trực tiếp khóa AES dưới dạng rõ.

\-Hỗ trợ xác thực và chữ ký số.



Mô hình tổng quát:



RSA

&#x20;|

&#x20;| Bảo vệ / trao đổi khóa

&#x20;v

AES

&#x20;|

&#x20;| Mã hóa dữ liệu lớn

&#x20;v

Dữ liệu được bảo vệ



Vì vậy, RSA và AES bổ sung cho nhau thay vì thay thế hoàn toàn cho nhau.



**7. KẾT LUẬN**



DES, AES và RSA là những thuật toán quan trọng trong lĩnh vực an toàn và bảo mật thông tin.



DES là thuật toán mã hóa đối xứng có lịch sử lâu đời, nhưng hiện nay không còn phù hợp với các yêu cầu bảo mật hiện đại do kích thước khóa hạn chế.



AES là thuật toán mã hóa đối xứng hiện đại, có tốc độ cao và khả năng bảo mật tốt. AES được sử dụng rộng rãi để mã hóa dữ liệu có kích thước lớn.



RSA là thuật toán mã hóa bất đối xứng sử dụng cặp khóa công khai và khóa bí mật. RSA có thể được sử dụng trong mã hóa, trao đổi khóa, xác thực và chữ ký số.



AES có tốc độ xử lý nhanh hơn RSA nên thường được sử dụng để mã hóa dữ liệu thực tế. RSA thường được sử dụng để trao đổi hoặc bảo vệ khóa AES và thực hiện các chức năng xác thực.



Việc kết hợp RSA và AES tạo thành mô hình mã hóa lai, trong đó RSA bảo vệ khóa AES còn AES đảm nhiệm việc mã hóa dữ liệu. Đây là cách tiếp cận hiệu quả để kết hợp ưu điểm của mã hóa đối xứng và bất đối xứng.

