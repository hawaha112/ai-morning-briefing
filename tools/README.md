# tools/ — HQ 口播音频离线重制

本仓(公开, Actions 分钟不限量)承担两段式口播的"慢引擎"步骤:
主仓 pg4_FUTURE 每班把口播文本推到 archive/data/broadcast-{shift}.txt + hq_job.json,
触发 .github/workflows/hq-audio.yml 用 Qwen3-TTS(0.6B, 纯 C 引擎, CPU ~75-90 分钟)
重制音频, 覆盖 archive/audio/ 同名 mp3(页面自动升级), 写 hq_done.json。
随后主仓 hq-tg-edit.yml 把 TG 消息音频原地替换。
tts_broadcast.py / bgm_loop.mp3(CC0) 是主仓的副本, 改动以主仓为准。
