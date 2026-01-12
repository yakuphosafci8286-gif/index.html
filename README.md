# index.html
<!DOCTYPE html>
<html lang="tr">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>Yakup Hoşafçı'nın AI Destekli Karikatür Portfolyosu</title>
  <style>
    :root {
      --bg: #0f0f12;
      --card: #16161a;
      --text: #eaeaea;
      --muted: #b8b8b8;
      --accent: #4cc9f0;
      --border: #26262b;
    }
    * { box-sizing: border-box; }
    html, body { margin: 0; padding: 0; background: var(--bg); color: var(--text); font-family: system-ui, -apple-system, Segoe UI, Roboto, Helvetica, Arial, sans-serif; }
    header {
      max-width: 1100px; margin: 24px auto; padding: 0 16px;
    }
    header h1 { margin: 0 0 8px; font-size: 1.8rem; }
    header p { margin: 0; color: var(--muted); }
    .grid {
      max-width: 1100px; margin: 24px auto; padding: 0 16px;
      display: grid; gap: 16px;
      grid-template-columns: repeat(auto-fill, minmax(240px, 1fr));
    }
    .item {
      background: var(--card); border: 1px solid var(--border); border-radius: 12px; overflow: hidden;
      transition: transform .2s ease, box-shadow .2s ease;
    }
    .item:hover { transform: translateY(-2px); box-shadow: 0 8px 24px rgba(0,0,0,.35); }
    .thumb {
      display: block; width: 100%; aspect-ratio: 4/3; object-fit: cover; background: #0b0b0d;
    }
    .meta { padding: 10px 12px; }
    .title { font-size: .95rem; margin: 0 0 4px; }
    .desc { margin: 0; color: var(--muted); font-size: .85rem; }
    footer {
      max-width: 1100px; margin: 24px auto 48px; padding: 0 16px; color: var(--muted); font-size: .9rem;
    }
    .brand { color: var(--accent); text-decoration: none; }
    /* Basit lightbox */
    .lightbox {
      position: fixed; inset: 0; background: rgba(0,0,0,.85);
      display: none; align-items: center; justify-content: center; padding: 24px; z-index: 9999;
    }
    .lightbox img { max-width: min(92vw, 1200px); max-height: 88vh; border-radius: 12px; }
    .lightbox.active { display: flex; }
    .close {
      position: fixed; top: 16px; right: 16px; background: var(--card); color: var(--text);
      border: 1px solid var(--border); border-radius: 999px; padding: 8px 12px; cursor: pointer;
    }
  </style>
</head>
<body>
  <header>
    <h1>Yakup Hoşafçı'nın AI Destekli Karikatür Portfolyosu</h1>
    <p>Toplumsal eleştiri, mizah ve evrensel temalar üzerine AI destekli karikatürler.</p>
  </header>

  <main class="grid">
    <!-- Görselleri buraya ekle: src yolunu kendi dosya yapına göre düzenle -->
    <figure class="item">
      <img class="thumb" src="1.jpg" alt="Karikatür 1" loading="lazy">
      <figcaption class="meta">
        <p class="title">Karikatür 1</p>
        <p class="desc">AI destekli görsel hikâye.</p>
      </figcaption>
    </figure>

    <figure class="item">
      <img class="thumb" src="2.jpg" alt="Karikatür 2" loading="lazy">
      <figcaption class="meta">
        <p class="title">Karikatür 2</p>
        <p class="desc">Toplumsal eleştiri ve mizah.</p>
      </figcaption>
    </figure>

    <figure class="item">
      <img class="thumb" src="3.jpg" alt="Karikatür 3" loading="lazy">
      <figcaption class="meta">
        <p class="title">Karikatür 3</p>
        <p class="desc">Deneysel kompozisyon.</p>
      </figcaption>
    </figure>

    <!-- İstersen daha fazla ekle: 4.jpg, 5.jpg ... -->
  </main>

  <footer>
    <p>Canlı site: <a class="brand" href="https://yakuphosafci8286-gif.github.io">yakuphosafci8286-gif.github.io</a></p>
  </footer>

  <div class="lightbox" id="lightbox" aria-hidden="true">
    <button class="close" id="closeBtn" aria-label="Kapat">Kapat</button>
    <img id="lightImg" alt="">
  </div>

  <script>
    // Basit lightbox: küçük görsele tıklayınca büyük açılır
    const lightbox = document.getElementById('lightbox');
    const lightImg = document.getElementById('lightImg');
    const closeBtn = document.getElementById('closeBtn');

    document.querySelectorAll('.thumb').forEach(img => {
      img.addEventListener('click', () => {
        lightImg.src = img.src;
        lightImg.alt = img.alt;
        lightbox.classList.add('active');
        lightbox.setAttribute('aria-hidden', 'false');
      });
    });

    const close = () => {
      lightbox.classList.remove('active');
      lightbox.setAttribute('aria-hidden', 'true');
      lightImg.src = '';
    };

    closeBtn.addEventListener('click', close);
    lightbox.addEventListener('click', (e) => {
      if (e.target === lightbox) close();
    });
    document.addEventListener('keydown', (e) => {
      if (e.key === 'Escape') close();
    });
  </script>
</body>
</html>
