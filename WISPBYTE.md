# Wispbyte = WEBSITE + VIDEO (role.txt = web)
Ye zip sirf public site, pages, stream/video proxy aur images chalata hai. Crawler / AniList / TMDB ka bhaari kaam
yahan BAND hai (wo Cloady worker karta hai) - isliye 15% CPU me chalta hai.

Startup file: addon.py   |  Python 3.11+  |  pip install -r requirements.txt
Env (Wispbyte panel):
  SQL_URL, TOKEN_SECRET, ADMIN_KEY  -> Cloady wale zip ke SAME hone chahiye (wahi shared database)
  PROTECT=log   CF_TUNNEL_TOKEN=... (agar tunnel use kar rahe ho)
  PULL_SECONDS=300 (worker ka naya data kitni der me uthaye)  CPU_TARGET=12 (default)
Logs me "[pull] ... worker last seen X min ago" dikhna chahiye. "NEVER" = Cloady band hai ya SQL_URL alag hai.

## Cloady se jodna (processing wahan, bytes yahan)
  WORKER_URL=https://<cloady-ka-url>   (sirf ye server jaanta hai, users ko kabhi nahi dikhta)
Anime ka detail (meta), video-link nikalna (stream/watch) aur skip-intro ka kaam Cloady karta hai; browser sirf Wispbyte se
baat karta hai. Video, images, posters Wispbyte hi bhejta hai (Cloady par sirf chhota JSON jaata hai).
Cloady band/slow ho to 3 fail ke baad 1 min ke liye Wispbyte khud kar leta hai (RPC_FALLBACK=0 se ye band).
TOKEN_SECRET dono me same hona zaroori hai (call ka signature isi se bana hai).
