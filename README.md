# Cosmic-Vanguard
Game bắn súng không gian phong cách arcade cổ điển với thiết kế hiện đại
Tính năng • Cách chơi • Cài đặt • Điều khiển • Kiến trúc

📖 Tổng quan
Cosmic Vanguard là game bắn súng không gian được phát triển bằng Java, lấy cảm hứng từ các game arcade cổ điển như Space Invaders và các game bullet-hell hiện đại. Bảo vệ nhân loại trước những đợt tấn công ngày càng khó khăn của người ngoài hành tinh, thu thập power-ups và đối mặt với các trận boss khốc liệt.
🎯 Điểm nổi bật

Hệ thống độ khó tăng dần: Các đợt (waves) tự động tăng độ khó với chỉ số enemy cao hơn, pattern đạn phức tạp và số lượng địch nhiều hơn
Trận chiến Boss: Đối đầu hoành tráng với boss khổng lồ có pattern bắn đạn hình tròn
Hệ thống Power-Up: 6 loại power-up độc đáo bao gồm Bắn 3 Viên, Đạn Xuyên Thủng và Lá Chắn Năng Lượng
Đa dạng hình ảnh: 5 biến thể enemy và background xoay vòng qua các waves
Giao diện đẹp mắt: Menu rõ ràng, thanh HP, hiệu ứng hình ảnh và animation mượt mà


✨ Tính năng
🎮 Gameplay cốt lõi
Tính năngMô tảTiến trình theo WaveVô hạn waves với độ khó tăng theo cấp số nhânAI EnemyPattern di chuyển thông minh với đổi hướng ngẫu nhiên và phát hiện biênCơ chế BossPattern bắn hình tròn độc đáo với 8-16 viên đạn mỗi lầnHệ thống Va chạmPhát hiện hitbox chính xác cho đạn, enemy và người chơiHệ thống ĐiểmĐiểm được tính dựa trên loại enemy và số wave
💪 Power-Ups
Power-UpThời gianHiệu ứngTriple Shot10 giâyBắn 3 viên đạn theo pattern fan-shapedPiercing Bullets10 giâyĐạn xuyên qua tối đa 3 enemiesEnergy Shield15 giâyChặn 1 đòn tấn công + miễn sát thương tạm thờiHealth PackTức thìHồi 1 mạng (tối đa 5)Score BoostTức thì+100 điểmPower BonusTức thì+50 điểm
🎨 Hình ảnh & Âm thanh

5 Biến thể Enemy: Sprite độc đáo xoay vòng mỗi 5 waves
Background Động: Môi trường không gian theo chủ đề wave
Hiệu ứng Nổ: Animation particle mượt khi enemy chết
Hiệu ứng Âm thanh: Bắn, nổ, chết và âm thanh nút bấm
Nhạc nền: Soundtrack lặp lại liên tục
Thanh HP: Chỉ báo máu có màu sắc (Xanh lá → Vàng → Đỏ)


🎮 Cách chơi
Tiến trình Wave
Wave 1  → Hướng dẫn (8-12 enemies, 1 HP, chậm)
Wave 2  → 10 enemies, 1 HP
Wave 3  → 12 enemies, 2 HP, đạn nhanh hơn
Wave 5  → 16 enemies, 4 HP, nhiều viên đạn
Wave 10 → 20 enemies, 9 HP, độ khó cực cao
Boss    → Xuất hiện sau khi tiêu diệt hết enemy thường
Tăng độ khó
Các loại Enemy
Lưu ý: Phiên bản hiện tại chỉ spawn loại NORMAL và BOSS

🚀 Cài đặt
Yêu cầu hệ thống

Java JDK 8+ (khuyến nghị JDK 11+)
IDE Java bất kỳ (IntelliJ IDEA, Eclipse, VS Code với extension Java)

Hướng dẫn nhanh

Clone repository

bash   git clone https://github.com/yourusername/cosmic-vanguard.git
   cd cosmic-vanguard
```

2. **Cấu trúc thư mục**
```
   cosmic-vanguard/
   ├── src/
   │   └── spaceinvaders/
   │       ├── Main.java
   │       ├── GamePanel.java
   │       ├── Player.java
   │       ├── Enemy.java
   │       ├── WaveManager.java
   │       └── ... (các class khác)
   ├── resources/
   │   ├── images/
   │   │   ├── player.png
   │   │   ├── enemy1.png ~ enemy5.png
   │   │   ├── boss1.png ~ boss5.png
   │   │   └── ... (assets khác)
   │   └── sounds/
   │       ├── shoot.wav
   │       ├── explosion.wav
   │       └── ... (audio khác)
   └── README.md

## 🎮 Điều khiển

### Bàn phím

| Phím | Chức năng |
|------|-----------|
| **Phím mũi tên** | Di chuyển tàu (↑↓←→) |
| **SPACE** | Bắn |
| **P** | Tạm dừng/Tiếp tục |
| **ENTER** | Bắt đầu game / Chơi lại |
| **ESC** | Quay về menu |

### Chuột

- **Click vào nút** trên màn hình start/end
- **Hover** để xem hiệu ứng sáng nút

---

## 🏗️ Kiến trúc

### Design Patterns
```
┌─────────────────────────────────────────┐
│         Kiến trúc giống MVC             │
├─────────────────────────────────────────┤
│ Model:      Player, Enemy, Bullet, Item │
│ View:       Các phương thức draw()      │
│ Controller: GamePanel, InputHandler     │
└─────────────────────────────────────────┘

Singleton Pattern:
└─ AssetManager (quản lý tài nguyên)

Factory-like Pattern:
└─ WaveManager (tạo enemies)

State Pattern:
└─ GameState enum (START, PLAYING, PAUSED, END)
Game Loop
javaGamePanel.actionPerformed() // 60 FPS
   ↓
1. handleInput() → Đọc phím từ InputHandler
   ↓
2. update()
   ├─ Player.update()
   ├─ Enemy.update() × n
   ├─ Bullet.update() × n
   ├─ Item.update() × n
   └─ Explosion.update() × n
   ↓
3. checkCollisions()
   ├─ Player bullets × Enemies
   ├─ Enemy bullets × Player
   └─ Enemies × Player
   ↓
4. checkWaveProgress()
   ├─ WaveManager.checkAndSpawnBoss()
   └─ WaveManager.isWaveComplete()
   ↓
5. repaint() → Vẽ tất cả objects
```

### Luồng xử lý Wave
```
┌─────────────────────────────────────────┐
│          Wave Lifecycle                 │
└─────────────────────────────────────────┘

1. WaveManager.calculateWaveParameters()
   - Tính số lượng enemies
   - Tính stats (speed, HP, damage)
   - Lấy variant (1-5)

2. WaveManager.spawnWave()
   - Tạo enemies theo grid layout
   - Tất cả loại NORMAL

3. Gameplay
   - Player bắn enemies
   - Enemies di chuyển & bắn
   - Items rơi khi enemy chết (30% chance)

4. WaveManager.checkAndSpawnBoss()
   - Điều kiện: activeNormalCount = 0
   - Spawn Boss ở giữa màn hình

5. Boss Fight
   - Boss bắn circular pattern
   - Player phải né và bắn
   - Boss HP cao gấp 15-20 lần normal

6. WaveManager.isWaveComplete()
   - Kiểm tra: boss spawned? all dead?
   - True → nextWave()

7. Loop lại từ bước 1 với wave++
```

---

## 📊 Hệ thống Điểm

### Tính điểm

| Hành động | Điểm |
|-----------|------|
| **Tiêu diệt NORMAL** | 10 × level |
| **Tiêu diệt FAST** | 15 × level |
| **Tiêu diệt SHOOTING** | 25 × level |
| **Tiêu diệt BOSS** | 200 × level |
| **Nhặt Score Item** | +100 |
| **Nhặt Power Item** | +50 |

### Ví dụ
```
Wave 5:
- Tiêu diệt 16 NORMAL: 16 × (10 × 5) = 800 điểm
- Tiêu diệt BOSS: 200 × 5 = 1000 điểm
- 2 Score Items: 200 điểm
- Tổng Wave 5: 2000 điểm
```

---

## 🎯 Chiến thuật chơi

### Tips cho người mới

1. **Wave 1-2: Học cơ bản**
   - Tập di chuyển và bắn
   - Enemy chỉ có 1 HP → dễ tiêu diệt
   - Không vội vã

2. **Wave 3-5: Quản lý Power-ups**
   - Ưu tiên nhặt Shield và Triple Shot
   - Giữ khoảng cách với enemies
   - Chú ý đạn enemy

3. **Wave 6-10: Chiến thuật nâng cao**
   - Di chuyển liên tục
   - Không đứng yên quá 1 giây
   - Focus boss ngay khi xuất hiện

4. **Boss Fight**
   - Đứng ở dưới màn hình
   - Di chuyển qua khe hở giữa các đạn
   - Dùng Shield nếu có
   - Bắn liên tục

### Priority target
```
Trong wave:
1. Enemies gần player nhất (tránh collision)
2. Enemies có HP thấp (easy kill)
3. Enemies còn lại

Boss fight:
- 100% focus vào Boss
- Né đạn > deal damage
- Sống sót là ưu tiên số 1
```

## 📚 Tài liệu kỹ thuật

### Nghiệp vụ hệ thống Enemy

**Enemy Movement AI:**
- Di chuyển random theo pattern X-Y
- Đổi hướng mỗi 60 frames (1 giây)
- Bounce khi chạm biên màn hình
- Vertical speed = 30% horizontal speed

**Boss Movement:**
- Di chuyển hình sin (sine wave)
- Rơi xuống 1 pixel mỗi giây
- Luôn ở phía trên màn hình

**Shooting Mechanics:**
- Normal enemies: 1-3 đạn thẳng (tùy level)
- Boss: 8-16 đạn circular pattern
- Shoot interval giảm theo level
- Rotation +10° mỗi lần bắn (boss)

### Power-up Drop System
```
Enemy chết:
├─ 30% chance spawn item
├─ Random loại item:
│  ├─ 25% TRIPLE_SHOT
│  ├─ 25% PIERCING
│  ├─ 25% SHIELD
│  ├─ 15% HEALTH
│  └─ 10% SCORE
└─ Item rơi xuống + xoay 360°
```

### Collision Detection
```
Mỗi frame:
├─ Check player bullets × enemies
│  → Enemy.takeDamage()
│  → Nếu HP=0: spawn Explosion + Item
├─ Check enemy bullets × player
│  → Player.takeDamage()
│  → Check shield → Check invincibility
└─ Check enemies × player
   → Cả hai nhận damage
```

---

## 🤝 Đóng góp

Mọi đóng góp đều được chào đón! Nếu bạn muốn:

1. **Báo lỗi**: Tạo Issue mô tả chi tiết
2. **Đề xuất tính năng**: Tạo Issue với tag `enhancement`
3. **Gửi code**: Fork repo → tạo branch → Pull Request

### Ý tưởng cải tiến

- [ ] Thêm enemy types FAST và SHOOTING
- [ ] Hệ thống achievements/trophies
- [ ] Leaderboard lưu high scores
- [ ] Nhiều boss patterns hơn
- [ ] Multiplayer local co-op
- [ ] Bullet time slow-motion effect
- [ ] Weapon upgrade system
- [ ] Story mode với cutscenes

---

## 📜 License

Dự án này được phát hành dưới [MIT License](LICENSE).
```
MIT License

Cosmic Vanguard

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction...

👨‍💻 Tác giả
Tên dự án: Cosmic Vanguard
Ngôn ngữ: Java + Swing
Thể loại: Arcade Shooter
Năm: 2025

🙏 Cảm ơn

Space Invaders (1978) - Inspiration
Touhou Project - Bullet pattern inspiration
Java Swing - UI framework
Community - Feedback và support

🌟 Nếu thích project này, hãy cho 1 star! 🌟

