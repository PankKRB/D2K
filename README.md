## 📋 **THÔNG TIN CHUNG**

### 🔧 **Hỗ trợ phiên bản:**
- **Minecraft:** 1.20+
- **Java:** 1.8+
- **Spigot/Paper:** ✅ Hỗ trợ đầy đủ
- **Folia:** ✅ Hỗ trợ chính thức
- **PurPur:** ✅ Tương thích

### 🔌 **Plugin tương thích:**
- **PlaceholderAPI:** ✅ Hỗ trợ đầy đủ (xem chi tiết bên dưới)
- **Vault:** Không bắt buộc (plugin tự quản lý economy)
- **DiscordSRV:** Tương thích (webhook riêng)

### ⚠️ **Khả năng xung đột:**
**✅ KHÔNG XUNG ĐỘT với:**
- **Economy plugins:** EssentialsX, CMI, Vault-based plugins
- **Protection plugins:** WorldGuard, GriefPrevention, Residence
- **Chat plugins:** EssentialsChat, ChatManager, VentureChat
- **Permission plugins:** LuckPerms, PermissionsEx, GroupManager
- **Multi-world plugins:** Multiverse, MyWorlds
- **Anti-cheat plugins:** AAC, Matrix, Spartan

**🔧 TƯƠNG THÍCH ĐẶC BIỆT:**
- **Folia:** ✅ Native support với SchedulerHelper
- **Paper/Spigot:** ✅ Optimized cho cả hai
- **MySQL plugins:** Tương thích database pooling
- **Webhook plugins:** Sử dụng port riêng (offset +1000)

**⚡ THIẾT KẾ TRÁNH XUNG ĐỘT:**
- **Commands:** Chỉ đăng ký `/atm` và `/napthe` (unique)
- **Events:** Chỉ listen events cần thiết, không override
- **Database:** SQLite riêng biệt, không ảnh hưởng plugins khác  
- **Port:** Auto-detect và offset để tránh conflict
- **Dependencies:** Self-contained, không require external plugins

---

## 🎯 **TÍNH NĂNG CHÍNH**

### 💳 **1. Nạp tiền qua ngân hàng (ATM)**
- **Cổng thanh toán:** SePay
- **Tạo QR tự động** cho từng giao dịch
- **Webhook real-time** nhận thông báo thanh toán
- **Mốc nạp:** 10K → 10M VND
- **Phần thưởng tự động** khi nạp thành công

### 🎫 **2. Nạp thẻ cào**
- **API:** Card2K.com
- **Nhà mạng:** Viettel, Mobifone, Vinaphone, Vietnamobile, Garena, Gate, Zing, VTC...
- **Validate thông minh** theo từng nhà mạng
- **Chống spam:** Giới hạn thẻ sai (ngày/liên tục)
- **GUI thân thiện** với người dùng

### 📊 **3. Top nạp tiền**
- **Bảng xếp hạng** người nạp nhiều nhất
- **Multi-server** (MySQL support)
- **GUI hiển thị** top donators
- **PlaceholderAPI** đầy đủ

### 🛡️ **4. Bảo mật**
- **Permission system** chi tiết
- **API Key authentication** cho webhook
- **IP whitelist** cho SePay
- **Audit logging** đầy đủ

---

## 📊 **PLACEHOLDERAPI - TOP NẠP TIỀN**

### 🏆 **Top Donators Placeholders**

Plugin hỗ trợ đầy đủ PlaceholderAPI với các placeholder sau:

#### **Top theo thời gian:**
```
%d2k_top_day_<server>_<rank>%     - Top ngày
%d2k_top_week_<server>_<rank>%    - Top tuần  
%d2k_top_month_<server>_<rank>%   - Top tháng
%d2k_top_all_<server>_<rank>%     - Top tổng
```

**Ví dụ:**
- `%d2k_top_day_lobby_1%` → Top 1 ngày server lobby
- `%d2k_top_month_survival_3%` → Top 3 tháng server survival
- `%d2k_top_all_hub_10%` → Top 10 tổng server hub

#### **Tổng nạp cá nhân:**
```
%d2k_total_<server>%              - Tổng nạp của player hiện tại
%d2k_total_<server>_<player>%     - Tổng nạp của player cụ thể
%d2k_total_raw_<server>_<player>% - Tổng nạp (số thuần, không format)
```

**Ví dụ:**
- `%d2k_total_lobby%` → "1,500,000 VND"
- `%d2k_total_lobby_hoangkiet%` → "2,000,000 VND"  
- `%d2k_total_raw_lobby_hoangkiet%` → "2000000"

### 📈 **Cấu hình Top Donators**

**File:** `config.yml`
```yaml
# Nguồn dữ liệu để lấy top nạp
top-donators-source: "mysql" # "mysql" hoặc "yml"

# Tên server (để phân biệt khi dùng MySQL multi-server)
server-name: LOBBY
```

**Lưu ý:**
- **MySQL:** Khuyến nghị cho network nhiều server
- **YML:** Phù hợp cho single server
- **Cache:** Tự động refresh mỗi phút
- **Performance:** Optimized queries với index

---

## 🎮 **LỆNH VÀ QUYỀN**

### 📝 **Lệnh chính:**
```
/atm                    - Mở GUI nạp tiền
/atm top               - Xem top donators
/atm status            - Kiểm tra trạng thái (admin)
/atm reload            - Reload config (admin)

/napthe                - Mở GUI nạp thẻ
/napthe <nhà_mạng> <mệnh_giá> <mã_thẻ> <serial>
/napthe stats          - Thống kê giới hạn thẻ sai (admin)
```

### 🔐 **Quyền hạn:**
```
# Người chơi thông thường
atm.use                - Sử dụng ATM
atm.balance            - Xem số dư
atm.history            - Xem lịch sử
atm.top                - Xem top donators
napthe.use             - Nạp thẻ cào

# Moderator
atm.history.others     - Xem lịch sử người khác
atm.balance.others     - Xem số dư người khác

# Admin
atm.reload             - Reload config
atm.toggle             - Bật/tắt chức năng
d2k.admin.basic        - Admin cơ bản
d2k.admin.full         - Admin đầy đủ (nguy hiểm)
```

---

## ⚙️ **CÀI ĐẶT VÀ CẤU HÌNH**

### 📦 **Cài đặt:**
1. Tải plugin D2K-x.x.x.jar
2. Đặt vào thư mục `/plugins/`
3. Khởi động server
4. Cấu hình trong `/plugins/D2K/`

### 🔧 **File cấu hình:**
- `config.yml` - Cấu hình chính
- `atm-gui.yml` - GUI nạp tiền và phần thưởng
- `nap-card-gui.yml` - GUI nạp thẻ cào  
- `messages.yml` - Tin nhắn đa ngôn ngữ

### 🗄️ **Database:**
- **SQLite** (mặc định) - Single server
- **MySQL** (tùy chọn) - Multi-server network

---
### 🏆 **Mốc tích lũy:**
```yaml
milestones:
  enabled: true
  tiers:
    100000:    # 100K
      name: "&aMốc 100K"
      commands:
        - "give <player> diamond 5"
    1000000:   # 1M  
      name: "&6Mốc 1 Triệu"
      commands:
        - "give <player> diamond 60"
```

---

## 🔒 **BẢO MẬT**

### 🛡️ **SePay Webhook:**
- **API Key authentication**
- **IP whitelist** 
- **Timestamp validation**
- **Port security** (10000-60000)

### 🎫 **Card2K API:**
- **Partner authentication**
- **Request signing**
- **Rate limiting**
- **Error handling**

### 📊 **Audit Log:**
- Tất cả giao dịch được log
- Admin actions tracking
- Security events monitoring
- Database integrity checks

---

## 🚀 **PERFORMANCE**

### ⚡ **Tối ưu hóa:**
- **Async database operations**
- **Connection pooling** (HikariCP)
- **Cached placeholders** (1 phút)
- **Indexed queries**
- **Thread-safe operations**

### 🔄 **Folia Support:**
- **SchedulerHelper** wrapper
- **Region-aware operations**  
- **Thread-safe data structures**
- **Async-first design**
