## 1. Head elements


```html
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="Học HTML từ cơ bản đến nâng cao">
    <title>My First Web Page</title>
    <link rel="icon" href="favicon.ico" type="image/x-icon">
    <link rel="stylesheet" href="style.css">
</head>
```

### 1.1. `<meta>`

Thẻ `<meta>` dùng để khai báo metadata (siêu dữ liệu) cho trang HTML — thông tin mô tả về trang nhưng không hiển thị trực tiếp cho người dùng. Đây cũng là thẻ tự đóng (self-closing), đặt trong `<head>`.

```html
<!-- Cơ bản -->
<meta charset="UTF-8">

<!-- Đầy đủ -->
<meta name="description" content="Trang học HTML cơ bản" lang="vi">
```

Các thuộc tính chính:

- **charset**: khai báo bảng mã ký tự cho trang, nên đặt là thẻ `<meta>` đầu tiên trong `<head>` (trước cả `<title>`) để trình duyệt đọc đúng encoding ngay từ đầu. Giá trị gần như duy nhất được dùng hiện nay là `UTF-8`.

    ```html
    <meta charset="UTF-8">
    ```

- **name** + **content**: hai thuộc tính luôn đi cùng nhau — `name` khai báo loại metadata, `content` là giá trị tương ứng. Gồm các loại phổ biến:

    | `name` | Tác dụng | Ví dụ |
    |---|---|---|
    | `viewport` | Cấu hình hiển thị trên di động | `<meta name="viewport" content="width=device-width, initial-scale=1.0">` |
    | `description` | Mô tả trang, hiển thị trong kết quả tìm kiếm (SEO) | `<meta name="description" content="Học HTML từ cơ bản đến nâng cao">` |

    <details>
    <summary>Xem thêm các loại <code>name</code> khác</summary>

    | `name` | Tác dụng | Ví dụ |
    |---|---|---|
    | `keywords` | Từ khóa liên quan tới trang — SEO, nhưng hiện gần như không còn tác dụng với Google | `<meta name="keywords" content="html, css, javascript">` |
    | `author` | Tác giả của trang | `<meta name="author" content="Nguyen Van A">` |
    | `robots` | Điều khiển crawler có index trang / theo link trong trang hay không | `<meta name="robots" content="noindex, nofollow">` |
    | `theme-color` | Màu thanh địa chỉ trình duyệt trên di động | `<meta name="theme-color" content="#317EFB">` |
    | `generator` | Công cụ/nền tảng tạo ra trang (VD: CMS) | `<meta name="generator" content="WordPress 6.4">` |

    </details>

- **http-equiv** + **content**: mô phỏng hành vi của một HTTP response header ngay trong HTML, dùng khi không thể (hoặc không tiện) cấu hình header phía server.

    | `http-equiv` | Tác dụng | Ví dụ |
    |---|---|---|
    | `refresh` | Tự động tải lại hoặc chuyển hướng trang sau X giây | `<meta http-equiv="refresh" content="5; url=https://example.com">` |
    | `X-UA-Compatible` | Ép IE cũ dùng chế độ render mới nhất | `<meta http-equiv="X-UA-Compatible" content="IE=edge">` |

    <details>
    <summary>Xem thêm các loại <code>http-equiv</code> khác</summary>

    | `http-equiv` | Tác dụng | Ví dụ |
    |---|---|---|
    | `content-security-policy` | Khai báo chính sách bảo mật nội dung (CSP), hạn chế nguồn script/style được phép chạy | `<meta http-equiv="Content-Security-Policy" content="default-src 'self'">` |
    | `content-type` | Khai báo kiểu nội dung + charset — cách khai báo cũ trước khi có thuộc tính `charset` riêng | `<meta http-equiv="Content-Type" content="text/html; charset=UTF-8">` |

    </details>

- **property** (không thuộc chuẩn HTML, nhưng rất phổ biến — dùng cho Open Graph để kiểm soát nội dung hiển thị khi chia sẻ link lên mạng xã hội):

    ```html
    <meta property="og:title" content="Tiêu đề khi chia sẻ Facebook">
    <meta property="og:description" content="Mô tả ngắn gọn khi chia sẻ">
    <meta property="og:image" content="https://example.com/thumbnail.jpg">
    ```

### 1.2. `<link>`

Thẻ `<link>` dùng để liên kết trang HTML hiện tại với một tài nguyên bên ngoài (file CSS, favicon, font...). Đây là thẻ tự đóng (self-closing), đặt trong `<head>`, không có nội dung bên trong.

```html
<!-- Cơ bản -->
<link rel="stylesheet" href="style.css" type="text/css">

<!-- Đầy đủ -->
<link rel="stylesheet" href="style.css" type="text/css" media="screen" crossorigin="anonymous">
```

Các thuộc tính chính:

- **rel** (bắt buộc): khai báo mối quan hệ giữa trang hiện tại và tài nguyên được liên kết. Gồm các loại sau:

    | `rel` | Tác dụng | Ví dụ |
    |---|---|---|
    | `stylesheet` | Liên kết file CSS ngoài — phổ biến nhất | `<link rel="stylesheet" href="style.css">` |
    | `icon` | Favicon hiển thị trên tab trình duyệt | `<link rel="icon" href="favicon.ico" type="image/x-icon">` |

    <details>
    <summary>Xem thêm các loại <code>rel</code> khác</summary>

    | `rel` | Tác dụng | Ví dụ |
    |---|---|---|
    | `apple-touch-icon` | Icon khi thêm trang vào màn hình chính trên iOS | `<link rel="apple-touch-icon" href="icon-180.png">` |
    | `preload` | Tải trước một tài nguyên (font, ảnh, script...) để dùng sớm, tăng performance | `<link rel="preload" href="font.woff2" as="font" type="font/woff2" crossorigin>` |
    | `preconnect` | Mở kết nối sớm tới domain khác (DNS, TLS) trước khi cần tải tài nguyên từ đó | `<link rel="preconnect" href="https://fonts.googleapis.com">` |
    | `dns-prefetch` | Phân giải DNS trước cho domain ngoài, tối ưu tốc độ | `<link rel="dns-prefetch" href="https://example.com">` |
    | `manifest` | Liên kết file manifest cho Progressive Web App (PWA) | `<link rel="manifest" href="manifest.json">` |
    | `canonical` | Khai báo URL "chính thức" của trang, tránh trùng lặp nội dung (SEO) | `<link rel="canonical" href="https://example.com/page">` |
    | `alternate` | Liên kết phiên bản khác của trang (ngôn ngữ khác, RSS feed...) | `<link rel="alternate" hreflang="vi" href="https://example.com/vi">` |
    | `author` | Liên kết tới trang/thông tin tác giả | `<link rel="author" href="humans.txt">` |

    </details>

- **href**: đường dẫn tới tài nguyên được liên kết — có thể là đường dẫn tương đối (`style.css`, `./assets/favicon.ico`) hoặc tuyệt đối (`https://fonts.googleapis.com/...`).

- **type**: khai báo kiểu MIME của tài nguyên, giúp trình duyệt biết cách xử lý trước khi tải về. Ví dụ:
    - `text/css` — cho stylesheet
    - `image/x-icon` hoặc `image/png` — cho favicon

    <details>
    <summary>Xem thêm các loại <code>type</code> khác</summary>

    - `image/svg+xml` — favicon/icon định dạng `.svg`
    - `font/woff2` — cho file font (thường đi kèm `preload`)
    - `font/woff` — font web, định dạng cũ hơn `woff2`
    - `application/manifest+json` — file manifest cho PWA (`rel="manifest"`)
    - `application/rss+xml` — RSS feed (`rel="alternate"`)

    </details>

    Trên trình duyệt hiện đại, `type` thường **không bắt buộc** — trình duyệt tự nhận diện qua đuôi file hoặc header response, nên nhiều dự án bỏ qua thuộc tính này (VD chỉ viết `<link rel="stylesheet" href="style.css">` mà không cần `type="text/css"`).

- **crossorigin**: cần khai báo khi tải tài nguyên từ domain khác (VD: font từ Google Fonts) để trình duyệt xử lý đúng CORS, đặc biệt quan trọng khi dùng với `rel="preload"`. Gồm các giá trị sau:

    | Giá trị | Ý nghĩa | Ví dụ |
    |---|---|---|
    | `anonymous` | Gửi request CORS **không kèm** thông tin xác thực (cookie, client cert...). Đây cũng là giá trị mặc định nếu chỉ viết `crossorigin` mà không kèm giá trị | `<link rel="preload" href="font.woff2" as="font" crossorigin>` |
    | `use-credentials` | Gửi request CORS **có kèm** thông tin xác thực — dùng khi server yêu cầu credentials mới trả về đúng tài nguyên | `<link rel="stylesheet" href="https://cdn.example.com/style.css" crossorigin="use-credentials">` |

    > Nếu bỏ hẳn thuộc tính `crossorigin`, trình duyệt tải tài nguyên như bình thường (không qua cơ chế CORS) — nhưng với font, trình duyệt **luôn** áp dụng CORS ẩn dù bạn không khai báo, nên nếu thiếu `crossorigin` mà server không cho phép, font sẽ tải thất bại âm thầm.

- **media**: chỉ định điều kiện (media query) để quyết định khi nào stylesheet được áp dụng. Một số giá trị phổ biến:

    | Giá trị | Ý nghĩa | Ví dụ |
    |---|---|---|
    | `all` | Áp dụng cho mọi thiết bị — **mặc định nếu không khai báo `media`** | `<link rel="stylesheet" href="style.css" media="all">` |
    | `screen` | Chỉ áp dụng khi xem trên màn hình (máy tính, điện thoại...) | `<link rel="stylesheet" href="style.css" media="screen">` |
    | `print` | Chỉ áp dụng khi in trang | `<link rel="stylesheet" href="print.css" media="print">` |
    | `speech` | Chỉ áp dụng cho trình đọc màn hình (screen reader) | `<link rel="stylesheet" href="speech.css" media="speech">` |

    <details>
    <summary>Xem thêm — kết hợp với media feature</summary>

    Có thể kết hợp `media` với các điều kiện chi tiết hơn (giống media query trong CSS):

    ```html
    <!-- Chỉ áp dụng khi màn hình rộng tối đa 600px -->
    <link rel="stylesheet" href="mobile.css" media="(max-width: 600px)">

    <!-- Chỉ áp dụng khi màn hình ở chế độ ngang -->
    <link rel="stylesheet" href="landscape.css" media="(orientation: landscape)">
    ```

    </details>

- **sizes**: khai báo kích thước icon, không tự resize ảnh mà chỉ khai báo cho trình duyệt biết kích thước thật của file; thường dùng với `rel="icon"` hoặc `apple-touch-icon` khi có nhiều kích thước khác nhau:
    ```html
    <link rel="icon" href="icon-32.png" sizes="32x32">
    ```