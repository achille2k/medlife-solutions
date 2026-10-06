# Medlife Solutions — Static Landing Page for Cloudflare Pages

Trang landing page tĩnh hoàn chỉnh được crawl và tối ưu hóa từ B12 (`https://medlife-solutions-pte-ltd.b12sites.com/`), sẵn sàng deploy trực tiếp lên **Cloudflare Pages** với custom domain tùy ý.

---

## 📁 Cấu trúc thư mục

```text
medlife-solutions.com/
├── index.html                   # Trang chủ chính (đã làm sạch script B12, tối ưu SEO, asset nội bộ)
├── 404.html                     # Trang 404 tùy chỉnh chuẩn nhận diện thương hiệu
├── robots.txt                   # Cấu hình crawl cho Google / Bing bot
├── sitemap.xml                  # Sitemap cho domain
├── _headers                     # Cấu hình bảo mật & cache của Cloudflare Pages
├── _redirects                   # Cấu hình redirect URL (/index -> /)
└── assets/
    ├── css/
    │   └── style.css            # Stylesheet chính đã được crawl về nội bộ
    ├── images/
    │   ├── logo.svg             # Logo vector chính thức (gốc từ Logo.pdf / Logo.ai)
    │   ├── logo.png             # Logo PNG nền trong suốt độ phân giải cao
    │   ├── logo-white.svg       # Logo vector phiên bản trắng cho nền tối
    │   ├── logo-white.png       # Logo PNG trắng cho nền tối
    │   ├── favicon.svg          # Favicon vector monogram M≡ chuẩn nhận diện
    │   ├── favicon-32x32.png    # Favicon PNG 32x32
    │   ├── favicon-192x192.png  # Favicon PNG 192x192
    │   ├── apple-touch-icon.png # Icon cho thiết bị iOS / bookmark (512x512)
    │   ├── hero.jpg             # Ảnh bìa Hero cảng biển Đông Nam Á
    │   ├── pillar-infrastructure.jpg # Trụ cột 01: Infrastructure
    │   ├── pillar-green-supply.jpg   # Trụ cột 02: Green Supply
    │   ├── pillar-healthcare.jpg     # Trụ cột 03: Healthcare
    │   └── pillar-food-supply.jpg    # Trụ cột 04: Food Supply
    └── docs/
        └── Medlife_Solutions_Company_Profile.pdf # File hồ sơ năng lực tải trực tiếp
```

---

## 🚀 Hướng dẫn đưa lên Cloudflare Pages & Custom Domain

Có 2 cách cực kỳ nhanh chóng để đưa trang lên Cloudflare Pages:

### Cách 1: Kết nối trực tiếp qua GitHub (Khuyên dùng)

1. **Commit & Push** toàn bộ mã nguồn này lên repo GitHub của bạn:
   ```bash
   git add .
   git commit -m "Deploy landing page for Cloudflare Pages"
   git push origin main
   ```
2. Mở [Cloudflare Dashboard](https://dash.cloudflare.com/) > chọn **Workers & Pages** > **Create application** > chọn tab **Pages** > **Connect to Git**.
3. Chọn repo `medlife-solutions.com`.
4. Cấu hình build:
   - **Framework preset**: `None`
   - **Build command**: *(để trống)*
   - **Build output directory**: `.` hoặc để trống (thư mục gốc).
5. Bấm **Save and Deploy**. Chỉ mất 10-15 giây là trang sẽ online trên subdomain dạng `xxx.pages.dev`.

---

### Cách 2: Deploy trực tiếp qua Direct Upload (Không cần build)

1. Mở Cloudflare Dashboard > **Workers & Pages** > **Create application** > tab **Pages** > **Upload assets**.
2. Đặt tên project (ví dụ: `medlife-solutions`).
3. Kéo thả toàn bộ thư mục này hoặc nén thành `.zip` và tải lên.
4. Bấm **Deploy site**.

---

### 🌐 Cấu hình Custom Domain (VD: `medlife-solutions.com`)

1. Trong dự án Pages trên Cloudflare, chọn tab **Custom domains**.
2. Bấm **Set up a custom domain**.
3. Nhập tên miền của bạn (ví dụ: `medlife-solutions.com` hoặc `www.medlife-solutions.com`).
4. **Nếu tên miền đã ở trên Cloudflare DNS**: Cloudflare sẽ tự động thêm bản ghi CNAME và cấp chứng chỉ SSL HTTPS miễn phí trong vài giây.
5. **Nếu tên miền ở nhà cung cấp khác** (Namecheap, GoDaddy, v.v.):
   - Cloudflare sẽ yêu cầu bạn trỏ 1 bản ghi CNAME:
     - **Name / Host**: `@` hoặc `www`
     - **Target / Value**: `<tên-project>.pages.dev`
6. Chờ vài phút để DNS kích hoạt và SSL hoàn tất!

---

## ⚡ Các điểm tối ưu đã thực hiện

1. **Độc lập 100%**: Toàn bộ ảnh độ phân giải cao và file tài liệu PDF đã được lưu cục bộ trong `assets/`, không còn phụ thuộc vào server B12 CDN.
2. **Loại bỏ tracking rác**: Đã xóa các script theo dõi nội bộ của B12, preview iframe error listener và reCAPTCHA thừa (trang không có form động, chỉ dùng mailto trực tiếp), giúp tăng tốc độ tải trang tối đa.
3. **Chuẩn Cloudflare**: Tích hợp sẵn `_headers` (bảo mật, cache vĩnh viễn cho assets) và `_redirects`.
