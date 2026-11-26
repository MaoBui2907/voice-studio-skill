# voice-studio

Skill cho agent dùng **TTS của runner** để làm voiceover: `VI = VieNeu v3 Nano` (Apache-2.0, 24kHz), `EN = Supertonic 3` (code MIT + weights OpenRAIL-M, 44.1kHz). Cả hai chạy offline trong image runner.

## Trạng thái

**Khung repo — chưa có nội dung skill.** Skill chỉ được viết sau khi PR của HYP-164 merge, vì contract của nó chính là flag/exit code thật của CLI `tts` trong runner. Viết trước là tài liệu nói dối.

- Task tạo skill: HYP-188 (project AI Tools), `blocked_by HYP-164`.
- Engine TTS + cách gọi CLI: xem repo `MaoBui2907/multica-agent-runner`, thư mục `runners/pi/tts/`.

## Ranh giới

- Skill **không** chứa model, không chứa logic suy luận. Model sống trong image runner.
- Nhạc nền/SFX: skill `audio-studio` (`MaoBui2907/audio-studio-skill`).
- Ghép hình: `video-studio`, `hyperframes`.
- Không có API cloud/trả phí — VI và EN đều offline.

## Sẽ có (khi HYP-164 xong)

- `SKILL.md` — khi nào dùng / không dùng, cách gọi `tts --lang vi|en`, preset giọng VI (mặc định `Mai Anh`, nam `Minh Quân`), ràng buộc offline, license.
- `scripts/` — wrapper gọi CLI runner, kiểm `ffprobe`, xử lý exit 3 (ngôn ngữ không có engine → **không fallback**).
- `tests/` — self-check + ca âm tính.
