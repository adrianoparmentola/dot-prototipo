[index.html](https://github.com/user-attachments/files/29085902/index.html)
<!DOCTYPE html>
<html lang="it">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1,user-scalable=no">
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/tabler-icons/3.31.0/tabler-icons.min.css">
<title>DOT — Un archivio per comunicare te stesso in sicurezza</title>
<style>
/* ═══════════════════════════════════════════════════════
   DOT DESIGN TOKENS — identità confermata
   iPhone 17: 402 × 874 pt logical
   ═══════════════════════════════════════════════════════ */
:root{
  --W:402px; --H:874px;

  /* Palette confermata */
  --navy:#2B2118;          /* testo, tab bar, ancore */
  --navy-soft:#4A3B2C;     /* testo secondario */
  --ice:#FAF4EC;           /* card / superfici calde */
  --ice-deep:#F4E6D2;      /* card insight tinta calda */
  --bg:#F3EBDF;            /* sfondo schermo */
  --orange:#D98324;        /* accento unico: CTA, attivo, segnale */
  --orange-soft:#F7E4CB;
  --orange-cta:#A85A0C;       /* CTA fill: bianco sopra = 5.08:1 (AA) */
  --orange-text:#8A5114;      /* testo/eyebrow/label arancio = 5.4-6.4:1 (AA) */
  --orange-deco:#D98324;      /* SOLO decorativo: icone, core, ombre */   /* fill tenue arancio */

  --muted:#6F5F4D;         /* caption / testo attenuato — su --bg ~4.6:1 (AA) */
  --line:rgba(43,33,24,.09);
  --line-orange:rgba(217,131,36,.26);

  /* Ombra firma: tasti sempre arancio 15% */
  --sh-btn:0 6px 16px rgba(217,131,36,.18);
  --sh-btn-strong:0 8px 22px rgba(217,131,36,.32);
  --sh-card:0 4px 18px rgba(43,33,24,.07);

  --r-card:20px; --r-pill:100px; --r-nav:26px;

  /* Bottom nav tenue: superficie ice elevata (Material: foglio sopra il contenuto) */
  --nav-surface:#FAF4EC;            /* ice — superficie chiara */
  --nav-ink:#2B2118;                /* icone/label attive */
  --nav-ink-off:#8A7B68;            /* inattive: su ice ~4.0:1 */
  --sh-nav:0 -2px 14px rgba(43,33,24,.10);  /* elevazione verso l'alto */

  --sf:-apple-system,BlinkMacSystemFont,"SF Pro Display","SF Pro Text","Segoe UI",sans-serif;
}
*,*::before,*::after{box-sizing:border-box;margin:0;padding:0;-webkit-tap-highlight-color:transparent}
html,body{background:#E2E2E2;min-height:100vh;min-height:100dvh;font-family:var(--sf);
  display:flex;align-items:center;justify-content:center;overflow-x:hidden}

/* ── PHONE ──────────────────────────────────────── */
.phone{
  width:var(--W);height:var(--H);max-height:100vh;max-height:100dvh;background:var(--bg);
  border-radius:54px;position:relative;overflow:hidden;
  box-shadow:0 0 0 12px #1a1a1c,0 0 0 13px #2a2a2c,0 50px 100px rgba(0,0,0,.4);
}
.island{position:absolute;top:13px;left:50%;transform:translateX(-50%);
  width:124px;height:36px;background:#000;border-radius:20px;z-index:300}

/* ── SCREEN SYSTEM ──────────────────────────────── */
.screen{position:absolute;inset:0;display:flex;flex-direction:column;
  transform:translateX(100%);transition:transform .32s cubic-bezier(.4,0,.2,1);
  will-change:transform;overflow:hidden;background:var(--bg)}
.screen.active{transform:translateX(0)}
.screen.exit-left{transform:translateX(-100%)}

/* ── STATUS BAR ─────────────────────────────────── */
.sb{height:59px;display:flex;align-items:flex-end;justify-content:space-between;
  padding:0 28px 11px;flex-shrink:0;position:relative;z-index:10}
.sb-t{font-size:15px;font-weight:600;color:var(--navy);letter-spacing:-.01em}
.sb-r{display:flex;align-items:center;gap:5px}
.sb-r svg{display:block}

/* ── BODY SCROLL ────────────────────────────────── */
.body{flex:1;min-height:0;overflow-y:auto;overflow-x:hidden;scrollbar-width:none;-webkit-overflow-scrolling:touch}
.body::-webkit-scrollbar{display:none}

/* ── DOT LOGOTYPE (o = onde concentriche) ───────── */
.dot-logo{display:inline-flex;align-items:center;font-weight:800;color:var(--navy);
  letter-spacing:-.03em;line-height:1}
.dot-logo .wave{display:inline-block;position:relative;border-radius:50%;
  background:var(--orange);flex-shrink:0}
.dot-logo .wave::before,.dot-logo .wave::after{content:'';position:absolute;
  border-radius:50%;border:1.5px solid rgba(255,255,255,.55)}
.dot-logo .wave::before{inset:22%}
.dot-logo .wave::after{inset:42%;background:rgba(255,255,255,.6);border:none}

/* concentric wave mark used as button/marker */
.wave-mark{position:relative;border-radius:50%;background:var(--orange);
  display:flex;align-items:center;justify-content:center;flex-shrink:0;
  background-image:repeating-radial-gradient(circle at center,
    rgba(255,255,255,.0) 0,rgba(255,255,255,.0) 3px,
    rgba(255,255,255,.32) 3px,rgba(255,255,255,.32) 4px)}

/* ── HEADERS ────────────────────────────────────── */
.scr-title{font-size:32px;font-weight:800;color:var(--navy);letter-spacing:-.02em;line-height:1}
.scr-sub{font-size:13px;color:var(--muted);line-height:1.5}
.eyebrow{font-size:11px;font-weight:700;letter-spacing:.14em;text-transform:uppercase;color:var(--orange-text)}
.sec-l{font-size:13px;font-weight:700;color:var(--navy);letter-spacing:-.01em}

/* top header row (title + avatar) */
.hdr-row{display:flex;align-items:center;justify-content:space-between;padding:6px 24px 14px}
.avatar{width:42px;height:42px;border-radius:50%;background:var(--orange-cta);
  display:flex;align-items:center;justify-content:center;
  font-size:17px;font-weight:700;color:#fff;cursor:pointer;flex-shrink:0;
  box-shadow:var(--sh-btn)}

/* ── BUTTONS ────────────────────────────────────── */
.btn{width:100%;padding:17px;border:none;border-radius:var(--r-pill);
  font-family:var(--sf);font-size:16px;font-weight:600;cursor:pointer;
  transition:transform .12s,box-shadow .18s;letter-spacing:-.01em}
.btn:active{transform:scale(.97)}
.btn-primary{background:var(--orange-cta);color:#fff;box-shadow:var(--sh-btn-strong)}
.btn-ghost{background:transparent;color:var(--navy);border:1.5px solid var(--line)}
.btn-soft{background:#fff;color:var(--navy);border:1.5px solid var(--line);box-shadow:var(--sh-card)}

/* ── CHIP FILTERS (Tutti / Attività / Sonno …) ──── */
.chips-row{display:flex;gap:8px;padding:0 24px 18px;overflow-x:auto;scrollbar-width:none}
.chips-row::-webkit-scrollbar{display:none}
.chip{padding:9px 18px;border-radius:var(--r-pill);font-size:13px;font-weight:600;
  cursor:pointer;white-space:nowrap;flex-shrink:0;transition:all .15s;
  background:#E9E6E1;color:var(--muted);border:none}
.chip.on{background:var(--orange-cta);color:#fff;box-shadow:var(--sh-btn)}

/* ── INSIGHT CARD (Home) ────────────────────────── */
.card{background:#fff;border-radius:var(--r-card);margin:0 24px 16px;
  box-shadow:var(--sh-card);overflow:hidden}
.card-ins{padding:18px}
.ins-meta{display:flex;align-items:center;gap:10px;margin-bottom:14px}
.ins-source{display:inline-flex;align-items:center;gap:6px;padding:6px 12px;
  border:1.5px solid var(--line-orange);border-radius:var(--r-pill);
  font-size:11px;font-weight:700;color:var(--navy)}
.ins-source .si{width:16px;height:16px;border-radius:4px;background:var(--orange-soft);
  display:flex;align-items:center;justify-content:center;font-size:10px}
.ins-ctx{font-size:11px;color:var(--muted);font-weight:500;
  border-bottom:1.5px solid var(--orange);padding-bottom:2px}
.ins-title{font-size:19px;font-weight:800;color:var(--navy);letter-spacing:-.02em;
  line-height:1.25;margin-bottom:8px}
.ins-body{font-size:14px;color:var(--navy-soft);line-height:1.5;margin-bottom:16px}
.ins-actions{display:flex;align-items:center;gap:12px}
.react-btn{width:38px;height:38px;border-radius:50%;border:none;background:transparent;
  cursor:pointer;display:flex;align-items:center;justify-content:center;
  transition:background .15s}
.react-btn svg{width:21px;height:21px;stroke:var(--navy);fill:none;stroke-width:1.6}
.react-btn.on svg{fill:var(--orange-text);stroke:var(--orange-text)}
.react-btn:hover{background:rgba(43,33,24,.05)}
.ins-cta{margin-left:auto;flex:1;max-width:200px;padding:13px;border:none;
  border-radius:var(--r-pill);background:var(--orange-cta);color:#fff;
  font-family:var(--sf);font-size:14px;font-weight:600;cursor:pointer;
  box-shadow:var(--sh-btn);transition:transform .12s}
.ins-cta:active{transform:scale(.96)}

/* ═══ HOME: frase dinamica ═══ */
.obs-phrase{font-size:26px;font-weight:800;color:var(--navy);letter-spacing:-.02em;line-height:1.15;max-width:280px}
.obs-phrase .hl{color:var(--orange-text)}

/* ═══ HOME: sfondo animato node-cloud (profondità + contrasto card) ═══ */
.home-bg{position:absolute;inset:0;z-index:0;overflow:hidden;pointer-events:none}
.home-bg canvas{position:absolute;left:50%;top:46%;transform:translate(-50%,-50%);
  width:175%;height:175%;
  filter:blur(11px) saturate(1.1);opacity:1}
/* velo morbido: stacca le card senza spegnere la nube */
.home-bg::after{content:"";position:absolute;inset:0;
  background:radial-gradient(ellipse at 50% 40%,rgba(243,235,223,.04) 0%,rgba(243,235,223,.42) 82%)}
/* il feed sta sopra lo sfondo */
.home-stack-wrap{position:relative;z-index:1}

/* home-source styles (legacy, non più usati) */
/* ═══ HOME: rimando laterale al DOT (sorgente delle insight) ═══ */
.home-source{position:absolute;top:0;right:-30px;height:100%;width:80px;z-index:0;
  display:flex;flex-direction:column;align-items:center;pointer-events:none;opacity:.5}
.hs-sphere{position:sticky;top:40%;width:54px;height:54px;border-radius:50%;flex-shrink:0;
  box-shadow:0 0 30px rgba(217,131,36,.4)}
.hs-line{position:absolute;top:0;bottom:0;right:42px;width:1.5px;
  background:repeating-linear-gradient(to bottom,var(--line-orange) 0 5px,transparent 5px 11px)}
.hs-cap{position:sticky;top:calc(40% + 60px);font-size:11px;font-weight:700;letter-spacing:.14em;color:var(--orange-text)}

/* ═══ HOME: feed di insight card (tweet → portrait) ═══ */
.stack{padding:0 20px;display:flex;flex-direction:column;gap:14px;margin-top:4px}
.ins-card{background:#fff;border-radius:var(--r-card);box-shadow:var(--sh-card);
  overflow:hidden;border:1.5px solid transparent;transition:border-color .2s,box-shadow .25s}
.ins-card.open{border-color:var(--line-orange);box-shadow:0 10px 30px rgba(43,33,24,.10)}

/* ── CHIUSA = post Twitter: compatta, fonte + testo, niente bottone pesante ── */
.ins-head{width:100%;text-align:left;background:none;border:none;font-family:var(--sf);
  padding:15px 16px;cursor:pointer;display:block;position:relative}
.ins-head:focus-visible{outline:3px solid var(--orange-text);outline-offset:-3px;border-radius:var(--r-card)}
.ins-meta{display:flex;align-items:center;gap:8px;margin-bottom:9px}
.ins-source{display:inline-flex;align-items:center;gap:6px;padding:5px 11px;
  border:1.5px solid var(--line-orange);border-radius:var(--r-pill);
  font-size:12px;font-weight:700;color:var(--navy)}
.ins-source .si{width:17px;height:17px;border-radius:5px;background:var(--orange-soft);
  display:flex;align-items:center;justify-content:center;font-size:11px;color:var(--orange-text)}
.ins-ctx{font-size:12px;color:var(--muted);font-weight:500}
.ins-title{font-size:16px;font-weight:800;color:var(--navy);letter-spacing:-.01em;line-height:1.3;margin-bottom:4px;
  padding-right:26px}
.ins-peek{font-size:14px;color:var(--navy-soft);line-height:1.45;
  display:-webkit-box;-webkit-line-clamp:2;-webkit-box-orient:vertical;overflow:hidden}
.ins-card.open .ins-peek{-webkit-line-clamp:unset;overflow:visible}
/* affordance discreto: piccolo chevron in alto a destra, basso peso */
.ins-expand{position:absolute;top:15px;right:14px;width:22px;height:22px;display:flex;align-items:center;
  justify-content:center;color:var(--muted);opacity:.5;transition:transform .3s,opacity .2s}
.ins-card.open .ins-expand{transform:rotate(180deg);opacity:.8}
.ins-head:hover .ins-expand{opacity:.85}

/* ── ESPANSA = post portrait Figma 4:5: focus su FONTE + COSA PUOI FARE ── */
.ins-full{max-height:0;overflow:hidden;transition:max-height .42s cubic-bezier(.32,.72,0,1)}
.ins-card.open .ins-full{max-height:900px}
.full-illus{aspect-ratio:5/3;margin:0 16px 14px;border-radius:14px;overflow:hidden;
  display:flex;align-items:center;justify-content:center;position:relative}
.full-body{padding:0 16px 16px;font-size:15px;color:var(--navy-soft);line-height:1.6}
/* "Cosa potresti fare" = elemento a MASSIMO focus */
.full-reco{margin:0 16px 14px;padding:18px;background:var(--orange-soft);border-radius:16px;
  border:1.5px solid var(--line-orange);position:relative}
.full-reco .reco-l{display:flex;align-items:center;gap:7px;font-size:12px;font-weight:800;color:var(--orange-text);
  text-transform:uppercase;letter-spacing:.06em;margin-bottom:8px}
.full-reco .reco-l::before{content:"";width:9px;height:9px;border-radius:50%;background:var(--orange-cta)}
.full-reco .reco-t{font-size:16px;color:var(--navy);line-height:1.5;font-weight:500}
.full-reco .reco-t b{color:var(--orange-text);font-weight:800}
/* la FONTE/razionale = secondo focus, riquadro dedicato */
.full-rationale{margin:0 16px 16px;display:flex;align-items:flex-start;gap:10px;padding:13px 14px;
  background:var(--bg);border-radius:13px;font-size:13px;color:var(--navy-soft);line-height:1.5}
.full-rationale svg{flex-shrink:0;margin-top:1px}
.full-rationale b{color:var(--navy);font-weight:700}
.full-actions{display:flex;align-items:center;gap:8px;padding:0 16px 16px}
.react-btn{width:44px;height:44px;border-radius:50%;border:1.5px solid var(--line);background:#fff;
  cursor:pointer;display:flex;align-items:center;justify-content:center;transition:all .15s}
.react-btn svg{width:20px;height:20px;stroke:var(--navy);fill:none;stroke-width:1.7}
.react-btn.on{border-color:var(--orange);background:var(--orange-soft)}
.react-btn.on svg{fill:var(--orange-text);stroke:var(--orange-text)}
.full-cta{margin-left:auto;flex:1;max-width:180px;min-height:44px;padding:12px;border:none;
  border-radius:var(--r-pill);background:var(--orange-cta);color:#fff;font-family:var(--sf);
  font-size:14px;font-weight:600;cursor:pointer;box-shadow:var(--sh-btn)}
.full-cta:active{transform:scale(.97)}
.stack-hint{text-align:center;font-size:12px;color:var(--muted);padding:14px 0 2px}


/* ═══ PROFILO: completamento + calendario ═══ */
.cmp-row{padding:10px 0;border-bottom:1px solid var(--line)}
.cmp-row:last-child{border-bottom:none;padding-bottom:0}
.cmp-row:first-child{padding-top:0}
.cmp-head{display:flex;align-items:center;justify-content:space-between;margin-bottom:8px}
.cmp-name{font-size:15px;font-weight:700;color:var(--navy)}
.cmp-pct{font-size:14px;font-weight:800;color:var(--orange-text);font-variant-numeric:tabular-nums}
.cmp-bar{height:8px;background:rgba(43,33,24,.08);border-radius:5px;overflow:hidden}
.cmp-fill{height:100%;background:var(--orange-cta);border-radius:5px;transition:width .5s var(--ease)}
.cmp-note{font-size:12px;color:var(--muted);margin-top:7px}
/* calendario */
.cal-head{display:flex;align-items:center;justify-content:space-between;margin-bottom:14px}
.cal-title{font-size:15px;font-weight:800;color:var(--navy)}
.cal-nav{min-width:44px;min-height:44px;border:none;background:none;color:var(--navy);font-size:18px;cursor:pointer;display:flex;align-items:center;justify-content:center}
.cal-wd{display:grid;grid-template-columns:repeat(7,1fr);gap:4px;margin-bottom:8px}
.cal-wd span{text-align:center;font-size:11px;font-weight:700;color:var(--muted)}
.cal-grid{display:grid;grid-template-columns:repeat(7,1fr);gap:4px}
.cal-day{aspect-ratio:1;display:flex;flex-direction:column;align-items:center;justify-content:center;gap:3px;
  border-radius:10px;font-size:13px;font-weight:600;color:var(--navy);position:relative;cursor:pointer}
.cal-day.empty{visibility:hidden}
.cal-day.today{background:var(--orange-soft)}
.cal-day .cal-dot{width:6px;height:6px;border-radius:50%;background:rgba(43,33,24,.18)}
.cal-day.has .cal-dot{background:var(--orange-cta)}
.cal-legend{display:flex;align-items:center;gap:6px;justify-content:center;margin-top:14px;font-size:11px;color:var(--muted)}
.cal-legend .cal-dot{width:7px;height:7px;border-radius:50%;background:rgba(43,33,24,.18);display:inline-block}
.cal-legend .cal-dot.has{background:var(--orange-cta)}

/* ═══ MEMORIA A TERZI ═══ */
.net-third{position:relative;height:34vh;min-height:230px;max-height:300px;flex-shrink:0;overflow:hidden;
  background:radial-gradient(ellipse at 50% 38%, var(--ice-deep) 0%, var(--bg) 72%)}
.net-third #net-canvas{position:absolute;inset:0;width:100%;height:100%}
.net-third-apps{position:absolute;top:14px;left:0;right:0;display:flex;justify-content:center;gap:12px;z-index:4}
.net-third-reveal{position:absolute;left:20px;right:20px;bottom:14px;z-index:4;
  background:rgba(255,255,255,.78);backdrop-filter:blur(8px);border:1.5px solid var(--line);
  border-radius:14px;padding:11px 14px;text-align:center;font-size:12.5px;color:var(--navy-soft);line-height:1.45;box-shadow:var(--sh-card)}
.net-third-reveal b{color:var(--orange-text);font-weight:700}
.net-app{min-width:46px;min-height:46px;width:46px;height:46px;border-radius:14px;background:#fff;box-shadow:var(--sh-card);
  display:flex;align-items:center;justify-content:center;font-size:22px;color:var(--c,var(--navy));
  cursor:pointer;transition:transform .18s;border:1.5px solid rgba(43,33,24,.06)}
.net-app:active{transform:scale(.9)}
.net-app.ping{animation:appPing .6s ease}
@keyframes appPing{0%,100%{transform:scale(1)}40%{transform:scale(1.18);box-shadow:0 0 0 6px var(--line-orange)}}
.net-app.empty{background:transparent;border:1.5px dashed var(--line-orange);color:var(--orange-text);box-shadow:none;font-size:20px}

/* due terzi: nota + storico chat */
.vault-lower{flex:1;background:var(--bg);border-radius:24px 24px 0 0;margin-top:-20px;position:relative;z-index:5;padding:22px 0 20px}
.note-cta{display:flex;align-items:center;gap:14px;margin:0 24px 22px;padding:18px;width:calc(100% - 48px);
  background:var(--orange-soft);border:1.5px solid var(--line-orange);border-radius:18px;cursor:pointer;text-align:left;
  font-family:var(--sf);transition:transform .15s}
.note-cta:active{transform:scale(.99)}
.note-cta-ic{width:46px;height:46px;border-radius:13px;background:var(--orange-cta);color:#fff;
  display:flex;align-items:center;justify-content:center;font-size:22px;flex-shrink:0}
.note-cta-tx{display:flex;flex-direction:column;line-height:1.35;flex:1}
.note-cta-tx b{font-size:16px;font-weight:800;color:var(--navy)}
.note-cta-tx i{font-size:12px;font-style:normal;color:var(--orange-text)}
.note-cta-plus{font-size:20px;color:var(--orange-text)}
.vault-sec-h{display:flex;align-items:center;justify-content:space-between;padding:0 24px 14px}
.sec-link{background:none;border:none;font-family:var(--sf);font-size:13px;font-weight:700;color:var(--orange-text);cursor:pointer;min-height:44px}
.chat-history{display:flex;flex-direction:column;gap:10px;padding:0 24px}
.chist{display:flex;align-items:center;gap:13px;padding:14px 16px;background:#fff;border:1.5px solid var(--line);
  border-radius:16px;cursor:pointer;text-align:left;font-family:var(--sf);width:100%;box-shadow:var(--sh-card);transition:transform .12s}
.chist:active{transform:scale(.99)}
.chist-ic{width:40px;height:40px;border-radius:11px;background:var(--orange-soft);color:var(--orange-text);
  display:flex;align-items:center;justify-content:center;font-size:19px;flex-shrink:0}
.chist-tx{display:flex;flex-direction:column;line-height:1.35;flex:1;min-width:0}
.chist-tx b{font-size:15px;font-weight:700;color:var(--navy);white-space:nowrap;overflow:hidden;text-overflow:ellipsis}
.chist-tx i{font-size:12px;font-style:normal;color:var(--muted);white-space:nowrap;overflow:hidden;text-overflow:ellipsis}
.chist-t{font-size:11px;font-weight:600;color:var(--muted);flex-shrink:0;align-self:flex-start;margin-top:2px}

/* collegamento app con utilità */
/* collegamento app con utilità */
.app-connect{display:flex;flex-direction:column;gap:10px;padding:0 24px}
.ac-card{display:flex;align-items:center;gap:14px;padding:14px 16px;background:#fff;border-radius:16px;box-shadow:var(--sh-card)}
.ac-ic{width:42px;height:42px;border-radius:11px;background:var(--c,var(--navy));color:#fff;
  display:flex;align-items:center;justify-content:center;font-size:20px;flex-shrink:0}
.ac-n{font-size:15px;font-weight:700;color:var(--navy)}
.ac-u{font-size:12px;color:var(--muted);margin-top:1px}
.ac-u b{color:var(--navy-soft);font-weight:600}
.ac-btn{margin-left:auto;padding:9px 16px;border:1.5px solid var(--line-orange);border-radius:100px;
  background:var(--orange-soft);color:var(--orange-text);font-family:var(--sf);font-size:13px;font-weight:700;cursor:pointer;flex-shrink:0;transition:all .15s}
.ac-btn.done{background:var(--orange);color:#fff;border-color:var(--orange)}

/* nota contestualizzata */
/* nota contestualizzata */
.ctx-note{display:flex;align-items:center;gap:14px;margin:0 24px 20px;padding:16px;
  background:var(--orange-soft);border:1.5px solid var(--line-orange);border-radius:16px;cursor:pointer;transition:transform .15s}
.ctx-note:active{transform:scale(.99)}
.ctx-note-ic{width:42px;height:42px;border-radius:11px;background:var(--orange-cta);color:#fff;
  display:flex;align-items:center;justify-content:center;font-size:20px;flex-shrink:0}
.ctx-note-t{font-size:15px;font-weight:700;color:var(--navy)}
.ctx-note-s{font-size:12px;color:#7A4A12;margin-top:1px}

/* ═══ MEMORIA: rete nodale (vecchio) ═══ */
.net-stage{position:relative;height:230px;margin:4px 0 4px;flex-shrink:0}
#net-canvas{width:100%;height:100%;display:block}
.net-lbl{position:absolute;font-size:11px;font-weight:700;color:var(--muted);text-transform:uppercase;letter-spacing:.08em;line-height:1.3;text-align:center}
.net-lbl span{font-weight:600;text-transform:none;letter-spacing:0;color:var(--muted);opacity:.7}
.net-lbl-in{right:14px;top:50%;transform:translateY(-50%);text-align:right}
.net-lbl-out{left:14px;top:50%;transform:translateY(-50%);text-align:left;color:var(--orange-text)}
.net-lbl-out span{color:var(--orange-text);opacity:.85}
.net-lbl-core{left:50%;bottom:8px;transform:translateX(-50%);color:var(--orange-text);font-size:12px;letter-spacing:.18em}
.net-flow{padding:0 28px 8px;text-align:center;font-size:12.5px;color:var(--muted);line-height:1.5;flex-shrink:0}
.net-flow b{color:var(--navy);font-weight:700}

/* trigger list */
.trig-list{display:flex;flex-direction:column;gap:10px;padding:0 24px}
.trig{display:flex;align-items:center;gap:14px;padding:14px 16px;background:#fff;border-radius:16px;
  box-shadow:var(--sh-card);position:relative;overflow:hidden}
.trig-dot{position:absolute;left:0;top:0;bottom:0;width:4px;background:var(--orange)}
.trig-ic{width:38px;height:38px;border-radius:10px;background:var(--orange-soft);display:flex;align-items:center;justify-content:center;font-size:17px;flex-shrink:0;margin-left:4px}
.trig-n{font-size:15px;font-weight:700;color:var(--navy)}
.trig-s{font-size:12px;color:var(--muted);margin-top:1px}
.trig-go{margin-left:auto;font-size:11px;font-weight:700;color:var(--orange-text);letter-spacing:.04em;flex-shrink:0}

/* ── DOCUMENT CARD (Memoria) ────────────────────── */
.doc-scroll{display:flex;gap:14px;padding:0 24px 8px;overflow-x:auto;scrollbar-width:none}
.doc-scroll::-webkit-scrollbar{display:none}
.doc-card{flex-shrink:0;width:158px;height:178px;background:var(--ice-deep);
  border:1.5px solid var(--line-orange);border-radius:var(--r-card);
  padding:18px;cursor:pointer;display:flex;flex-direction:column;
  box-shadow:var(--sh-btn);transition:transform .15s}
.doc-card:active{transform:scale(.97)}
.doc-card.add{background:transparent;border:1.5px dashed var(--line-orange);
  align-items:center;justify-content:center;box-shadow:none}
.doc-icon{width:42px;height:42px;display:flex;align-items:center;justify-content:center}
.doc-icon svg{width:38px;height:38px;fill:var(--orange)}
.doc-dots{margin-left:auto;display:flex;flex-direction:column;gap:3px}
.doc-dots span{width:4px;height:4px;border-radius:50%;background:var(--navy)}
.doc-name{font-size:15px;font-weight:700;color:var(--navy);line-height:1.25;margin-top:auto}
.doc-time{font-size:12px;color:var(--muted);margin-top:4px}
.doc-add-plus{width:44px;height:44px;border-radius:50%;background:var(--orange-cta);
  display:flex;align-items:center;justify-content:center;color:#fff;
  font-size:24px;font-weight:300;box-shadow:var(--sh-btn);margin-bottom:8px}
.doc-add-l{font-size:13px;font-weight:600;color:var(--orange-text)}

/* ── DAY DATA ROW (Memoria) ─────────────────────── */
.data-row{display:flex;align-items:center;gap:16px;padding:16px 24px;
  border-bottom:1.5px solid var(--orange);margin:0 0}
.data-ico{width:36px;height:36px;flex-shrink:0;display:flex;align-items:center;justify-content:center}
.data-ico svg{width:32px;height:32px;stroke:var(--navy);fill:none;stroke-width:1.5}
.data-name{font-size:16px;font-weight:700;color:var(--navy)}
.data-time{font-size:13px;color:var(--muted);margin-top:2px}

/* ── WEEK STRIP (Memoria giorni 10–16) ──────────── */
.week{display:flex;gap:10px;padding:0 24px 20px;overflow-x:auto;scrollbar-width:none}
.week::-webkit-scrollbar{display:none}
.wd{display:flex;flex-direction:column;align-items:center;gap:8px;cursor:pointer;flex-shrink:0}
.wd-num{width:46px;height:46px;border-radius:50%;background:var(--navy);
  display:flex;align-items:center;justify-content:center;
  font-size:18px;font-weight:700;color:#fff;transition:background .15s}
.wd.on .wd-num{background:var(--orange-cta);box-shadow:var(--sh-btn)}
.wd-l{font-size:15px;font-weight:700;color:var(--navy)}

/* ── BOTTOM NAV: Home ← Dot ← Memoria — superficie tenue elevata ─ */
.bnav{height:92px;width:100%;box-sizing:border-box;
  display:flex;align-items:flex-start;
  justify-content:space-around;padding:14px 30px 0;
  position:absolute;bottom:0;left:0;right:0;
  background:var(--nav-surface);border-top:1px solid var(--line);
  border-radius:var(--r-nav) var(--r-nav) 0 0;box-shadow:var(--sh-nav);z-index:10}
/* rete nodale: ornamento attenuato, non compete con le icone */
.bnav-net{position:absolute;left:0;right:0;top:0;height:48px;pointer-events:none;z-index:0}
.bnav-net line{stroke:rgba(43,33,24,.07);stroke-width:1}
.bnav-net .node{fill:rgba(43,33,24,.14)}
.bnav-net .flux{fill:var(--orange);opacity:0}
.bnav.flowing .bnav-net .flux{animation:fluxMove 1.1s ease-in-out}
@keyframes fluxMove{
  0%{opacity:0;transform:translateX(0)}
  15%{opacity:1}
  85%{opacity:1}
  100%{opacity:0;transform:translateX(-160px)}
}
.bni{display:flex;flex-direction:column;align-items:center;gap:6px;cursor:pointer;
  min-width:56px;min-height:48px;transition:opacity .15s;position:relative;z-index:2}
.bni svg{width:24px;height:24px;stroke:var(--nav-ink-off);fill:none;stroke-width:1.8}
.bni-l{font-size:11px;font-weight:600;color:var(--nav-ink-off)}
.bni.on svg{stroke:var(--orange-text)}
.bni.on .bni-l{color:var(--orange-text);font-weight:700}

/* DOT center button — FAB: pieno arancio, distinto dal wave-mark decorativo */
.dot-btn-w{display:flex;flex-direction:column;align-items:center;gap:6px;
  cursor:pointer;margin-top:-30px;position:relative;z-index:3}
.dot-btn{width:64px;height:64px;border-radius:50%;
  background:var(--orange-cta);
  display:flex;align-items:center;justify-content:center;
  box-shadow:0 0 0 5px var(--nav-surface),0 6px 18px rgba(217,131,36,.42);
  transition:transform .18s}
.dot-btn svg{width:26px;height:26px;stroke:#fff;fill:none;stroke-width:2;stroke-linecap:round;stroke-linejoin:round}
.dot-btn:active{transform:scale(.93)}
.dot-btn-l{font-size:11px;font-weight:600;color:var(--nav-ink)}

/* ═══ AUTH / ONBOARDING shared ═══ */
.pad{padding:0 28px}
.center-col{flex:1;display:flex;flex-direction:column;align-items:center;
  justify-content:center;padding:0 36px;text-align:center}
.input{width:100%;height:54px;background:#fff;border:1.5px solid var(--line);
  border-radius:14px;padding:0 18px;color:var(--navy);font-family:var(--sf);
  font-size:15px;outline:none;transition:border-color .18s;margin-bottom:12px}
.input::placeholder{color:var(--muted)}
.input:focus{border-color:var(--orange)}
.social-btn{width:100%;height:54px;border:1.5px solid var(--line);border-radius:var(--r-pill);
  background:#fff;color:var(--navy);font-family:var(--sf);font-size:15px;font-weight:600;
  cursor:pointer;display:flex;align-items:center;justify-content:center;gap:10px;
  margin-bottom:12px;box-shadow:var(--sh-card)}
.divider{display:flex;align-items:center;gap:14px;margin:16px 0;width:100%}
.divider::before,.divider::after{content:'';flex:1;height:1.5px;background:var(--line)}
.divider span{font-size:12px;color:var(--muted)}

/* progress dots onboarding */
.ob-dots{display:flex;gap:8px;justify-content:center;padding:18px 0 0}
.ob-dot{width:8px;height:8px;border-radius:50%;background:rgba(43,33,24,.15);transition:all .3s}
.ob-dot.on{background:var(--orange);width:24px;border-radius:5px}


/* progress bar profilazione */
.pbar{flex:1;height:6px;background:rgba(43,33,24,.1);border-radius:3px;overflow:hidden;margin-left:4px}
.pbar-fill{height:100%;background:var(--orange);border-radius:3px;transition:width .4s cubic-bezier(.4,0,.2,1)}

/* selectable list (Attività praticate ecc.) */
.sel-list{display:flex;flex-direction:column;gap:12px;padding:0 24px}
.sel-item{display:flex;align-items:center;padding:18px 20px;background:#fff;
  border:1.5px solid var(--line);border-radius:16px;cursor:pointer;
  font-size:16px;font-weight:600;color:var(--navy);transition:all .15s;box-shadow:var(--sh-card)}
.sel-item .ck{width:24px;height:24px;border-radius:50%;border:2px solid var(--line);
  margin-left:auto;flex-shrink:0;transition:all .15s;position:relative}
.sel-item.on{border-color:var(--orange)}
.sel-item.on .ck{background:var(--orange-cta);border-color:var(--orange-cta)}
.sel-item.on .ck::after{content:'';position:absolute;inset:6px;border-radius:50%;background:#fff}

/* ── DRUM PICKER (Età / Peso / Altezza) ─────────── */
.drum-area{flex:1;display:flex;align-items:center;justify-content:center;position:relative;padding:20px}
.drum-sel{position:absolute;left:48px;right:48px;height:72px;top:50%;transform:translateY(-50%);
  background:var(--ice-deep);border-radius:16px;pointer-events:none;z-index:1}
.drum-wrap{display:flex;align-items:center;gap:14px;position:relative;z-index:2}
.drum{height:288px;overflow-y:scroll;scroll-snap-type:y mandatory;scrollbar-width:none;width:140px;
  -webkit-overflow-scrolling:touch}
.drum::-webkit-scrollbar{display:none}
.drum-item{height:72px;display:flex;align-items:center;justify-content:center;
  scroll-snap-align:center;font-size:40px;font-weight:700;color:rgba(43,33,24,.2);
  transition:color .1s,font-size .1s;user-select:none}
.drum-item.selected{color:var(--orange-text);font-size:52px}
.drum-item.near{color:rgba(43,33,24,.45);font-size:44px}
.drum-unit{font-size:18px;font-weight:600;color:var(--muted)}
.drum-area::before,.drum-area::after{content:'';position:absolute;left:0;right:0;
  height:120px;z-index:3;pointer-events:none}
.drum-area::before{top:0;background:linear-gradient(to bottom,var(--bg),transparent)}
.drum-area::after{bottom:0;background:linear-gradient(to top,var(--bg),transparent)}

/* ── AI CHAT ────────────────────────────────────── */
.ai-hdr{display:flex;align-items:center;gap:14px;padding:6px 24px 16px}
.ai-back{width:36px;height:36px;border-radius:50%;border:1.5px solid var(--line);
  background:#fff;cursor:pointer;display:flex;align-items:center;justify-content:center;
  font-size:18px;color:var(--navy);flex-shrink:0}
.chat-msgs{flex:1;padding:8px 24px;display:flex;flex-direction:column;gap:14px;
  overflow-y:auto;scrollbar-width:none}
.chat-msgs::-webkit-scrollbar{display:none}
.bubble-ai{max-width:82%;padding:14px 16px;background:#fff;border:1.5px solid var(--line);
  border-radius:6px 18px 18px 18px;font-size:14px;color:var(--navy);line-height:1.5;box-shadow:var(--sh-card)}
.bubble-ai strong{color:var(--orange-text);font-weight:700}
.bubble-user{max-width:82%;align-self:flex-end;padding:14px 16px;background:var(--navy);
  border-radius:18px 6px 18px 18px;font-size:14px;color:#fff;line-height:1.5}
.bubble-ts{font-size:11px;color:var(--muted);margin-top:5px}
.chat-inp-row{padding:12px 24px 28px;display:flex;gap:10px;align-items:center;
  border-top:1.5px solid var(--line);background:var(--bg)}
.chat-inp{flex:1;height:50px;background:#fff;border:1.5px solid var(--line);
  border-radius:var(--r-pill);padding:0 20px;font-family:var(--sf);font-size:14px;
  color:var(--navy);outline:none}
.chat-inp:focus{border-color:var(--orange)}
.send-btn{width:50px;height:50px;border-radius:50%;background:var(--orange-cta);border:none;
  cursor:pointer;display:flex;align-items:center;justify-content:center;
  box-shadow:var(--sh-btn);flex-shrink:0}
.preset-row{padding:8px 24px 4px;display:flex;gap:8px;overflow-x:auto;scrollbar-width:none}
.preset-row::-webkit-scrollbar{display:none}
.pchip{padding:10px 16px;border-radius:var(--r-pill);background:#fff;border:1.5px solid var(--line);
  font-size:13px;font-weight:600;color:var(--navy);white-space:nowrap;flex-shrink:0;cursor:pointer;
  box-shadow:var(--sh-card)}
.pchip.hi{background:var(--orange-soft);border-color:var(--line-orange);color:var(--orange-text)}

/* ── PROFILO ────────────────────────────────────── */
.prof-hero{display:flex;flex-direction:column;align-items:center;padding:10px 24px 24px}
.prof-av{width:88px;height:88px;border-radius:50%;background:var(--orange-cta);
  display:flex;align-items:center;justify-content:center;font-size:36px;font-weight:700;
  color:#fff;box-shadow:var(--sh-btn-strong);margin-bottom:14px}
.prof-name{font-size:24px;font-weight:800;color:var(--navy);letter-spacing:-.02em}
.prof-meta{font-size:13px;color:var(--muted);margin-top:3px}
.prof-card{margin:0 24px 14px;background:#fff;border-radius:var(--r-card);box-shadow:var(--sh-card);overflow:hidden}
.prof-sec-l{font-size:12px;font-weight:700;letter-spacing:.1em;text-transform:uppercase;
  color:var(--muted);padding:0 24px;margin:8px 0 12px}
.prof-row{display:flex;align-items:center;gap:14px;padding:16px 18px;border-bottom:1.5px solid var(--line);cursor:pointer}
.prof-row:last-child{border-bottom:none}
.pri-ico{width:38px;height:38px;border-radius:10px;background:var(--orange-soft);
  display:flex;align-items:center;justify-content:center;font-size:17px;flex-shrink:0}
.pri-name{font-size:15px;font-weight:600;color:var(--navy)}
.pri-sub{font-size:12px;color:var(--muted);margin-top:1px}
.pri-badge{margin-left:auto;padding:5px 12px;border-radius:var(--r-pill);font-size:11px;font-weight:700}
.pri-badge.on{background:var(--orange-soft);color:var(--orange-text)}
.pri-badge.off{background:#E9E6E1;color:var(--muted)}

/* phenotype score tiles */
.phen-grid{display:flex;gap:12px;padding:0 24px 16px}
.phen-tile{flex:1;background:#fff;border-radius:18px;padding:16px;box-shadow:var(--sh-card);text-align:center}
.phen-val{font-size:30px;font-weight:800;color:var(--orange-text);letter-spacing:-.02em}
.phen-lbl{font-size:11px;font-weight:600;color:var(--muted);margin-top:3px;text-transform:uppercase;letter-spacing:.06em}

/* ── DOT OVERLAY (bottom sheet) ─────────────────── */
.overlay{position:absolute;inset:0;background:rgba(43,33,24,.4);z-index:250;
  opacity:0;pointer-events:none;transition:opacity .3s;display:flex;align-items:flex-end}
.overlay.open{opacity:1;pointer-events:auto}
.ovl-sheet{width:100%;background:var(--bg);border-radius:28px 28px 0 0;
  max-height:78%;display:flex;flex-direction:column;transform:translateY(100%);
  transition:transform .34s cubic-bezier(.4,0,.2,1);padding-bottom:20px}
.overlay.open .ovl-sheet{transform:translateY(0)}
.ovl-handle{width:40px;height:5px;border-radius:3px;background:rgba(43,33,24,.2);
  margin:12px auto;cursor:pointer;flex-shrink:0}
.ovl-hdr{display:flex;align-items:center;gap:12px;padding:0 24px 14px}
.ovl-title{font-size:18px;font-weight:800;color:var(--navy);letter-spacing:-.01em}
.ovl-close{margin-left:auto;width:34px;height:34px;border-radius:50%;border:none;
  background:#E9E6E1;color:var(--navy);font-size:15px;cursor:pointer}
.ovl-chat{flex:1;overflow-y:auto;padding:8px 24px;display:flex;flex-direction:column;gap:14px;scrollbar-width:none}
.ovl-chat::-webkit-scrollbar{display:none}
.ovl-inp-row{padding:12px 24px 0;display:flex;gap:10px;align-items:center}

.empty-note{text-align:center;padding:24px 0;font-size:15px;color:var(--muted);line-height:1.5}

/* ═══════════ ACCESSIBILITY FIXES ═══════════ */
/* Target tap minimi 44px su tutti gli interattivi piccoli */
.react-btn{min-width:44px;min-height:44px}
.chip,.nf-chip,.pchip{min-height:44px;display:inline-flex;align-items:center}
.ai-back{min-width:44px;min-height:44px}
.net-type{min-width:44px;min-height:44px}
.net-app{min-width:46px;min-height:46px}
.bni,.dot-btn-w{min-height:44px}
.pri-badge,.ac-btn,.m-conn-b{min-height:36px;display:inline-flex;align-items:center}
.doc-dots{min-width:44px;min-height:44px;justify-content:center}
.send-btn{min-width:44px;min-height:44px}
/* aumenta i testi sotto 12px che non siano label tracked */
.hs-cap{font-size:11px}
/* focus visibile da tastiera ovunque */
button:focus-visible,[role="button"]:focus-visible,[tabindex]:focus-visible,a:focus-visible,input:focus-visible,.chip:focus-visible,.bni:focus-visible{
  outline:3px solid var(--orange-text);outline-offset:2px;border-radius:6px}
/* rispetta prefers-reduced-motion: ferma rete nodale e transizioni */
@media (prefers-reduced-motion:reduce){
  *,*::before,*::after{animation-duration:.001ms!important;animation-iteration-count:1!important;transition-duration:.001ms!important}
  #net-canvas{opacity:.85}
}
/* screen-reader only helper */
.sr-only{position:absolute;width:1px;height:1px;padding:0;margin:-1px;overflow:hidden;clip:rect(0,0,0,0);white-space:nowrap;border:0}

</style>
</head>
<body>
<div class="phone">
<div class="island"></div>

<!-- ═══ SPLASH ═══ -->
<div class="screen" id="s-splash" style="transform:translateX(0)">
  <div class="sb"><span class="sb-t">9:41</span><span class="sb-r">
    <svg width="17" height="11" viewBox="0 0 17 11" fill="var(--navy)"><rect x="0" y="7" width="3" height="4" rx="1"/><rect x="4.5" y="5" width="3" height="6" rx="1"/><rect x="9" y="2.5" width="3" height="8.5" rx="1"/><rect x="13.5" y="0" width="3" height="11" rx="1"/></svg>
    <svg width="16" height="11" viewBox="0 0 16 12" fill="var(--navy)"><path d="M8 2.5c2 0 3.8.8 5.2 2l1.3-1.5C13 1.3 10.6.3 8 .3S3 1.3 1.5 3L2.8 4.5C4.2 3.3 6 2.5 8 2.5z"/><path d="M8 6c1 0 2 .4 2.7 1l1.3-1.5C10.9 4.5 9.5 4 8 4s-2.9.5-4 1.5L5.3 7C6 6.4 7 6 8 6z"/><circle cx="8" cy="9.5" r="1.6"/></svg>
    <svg width="25" height="12" viewBox="0 0 25 12"><rect x="1" y="1" width="21" height="10" rx="3" fill="none" stroke="var(--navy)" stroke-opacity=".4"/><rect x="3" y="3" width="16" height="6" rx="1.5" fill="var(--navy)"/><rect x="23" y="4" width="1.5" height="4" rx="1" fill="var(--navy)" fill-opacity=".4"/></svg>
  </span></div>
  <div class="center-col">
    <div style="font-size:30px;font-weight:800;color:var(--navy);letter-spacing:-.02em;margin-bottom:18px">Benvenut<span style="color:var(--orange)">*</span> in</div>
    <img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAZkAAACnCAYAAADDoiGnAAAACXBIWXMAAAsTAAALEwEAmpwYAAAAAXNSR0IArs4c6QAAAARnQU1BAACxjwv8YQUAAAAOdEVYdFNvZnR3YXJlAEZpZ21hnrGWYwAAml5JREFUeAHt/XuQXNl5Hwh+59x782bWu4AqAIUGuiEQBCmALZKC1BSplhqjdawpL3cndlbgeP7aoULmhtcjT3hjNBPWrAOFnfE6pJF2YqRdbixty3bEzmjdkHcidhVDz4TtQcttyqIHEqkmIBJdaqIb1Y1HFeqZVZl5H+fM9/vOOZm3qoFmdxbILgD36764N+8rb9465/zO73sS1VJLLbXUUksttdRSSy211FJLLbXUUksttdRSSy211FJLLbXUUksttdRSSy211FJLLbXUUksttdRSSy211FJLLbXUUksttdRSSy211FJLLbXUUksttdRSSy211FJLLbXUUksttdRSSy211FJLLbXUUksttdRSSy211FJLLbXUUksttdRSSy211FJLLbXUUksttfxQxFq7+7PilSzYrhwP+2up5aHi2w+k336q+yrLu9peLbXU8phLBUCCeDAZdP6LFy/qcF5YX7xImnYODDXg1CLyoDZVaS87FrQtvmL3/v51VEsttTz2oh6waD8o7FgwIFy4cCFyA8ODB41w08pMtZanS/qTELQBtJXQXsJ2+LyzLV3st6dwHQ0mMXVb2sdS/3FqeZhUAYHm55W6fv3CjvaytLS04/Ps7KwN+7B9+fJly4OBP3qJLl0iUBpLO9tdrf94egQAYbktATTo+vXrD2xPL730Er3yyiv99ZUrV6SNMOjQmTNn7CVuSGhW8/OMLkpV21Pdlvah1CBTyw4Js0LuvP19DBQqDAhhINjc3FTnzp2j1dVVNT39hl1dPdm/AJ+xvnFjXNYYLPh66wcIu/PrME6oenB4skWFuQUDhcbkAx/Onz8vbeb06dO8vkpoQ9PT03ZublXdvu3akNv3hg1tCZMXrP09+u0GE6G6He1PqUGmlt0ibYJnirIO7KUKLidPOkBpt9vq1CmihYXX6YUXXlQrK3elky8suBuNjY1ZDBo3btzYMUBUwaYeHJ58wUQCTBjbg/Z0WZ0+/WV19epVOnTokO50OrL/+edb/bawudlRd++6z2hLWKM94Rpugwaf0ZYcS4bh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" alt="DOT" style="height:130px;margin-bottom:24px;display:block">
    <div style="font-size:16px;color:var(--navy-soft);line-height:1.5;margin-bottom:48px">
      Un archivio per comunicare<br>te stesso in sicurezza<span style="color:var(--orange)">.</span>
    </div>
    <button class="btn btn-primary" style="max-width:240px" onclick="go('s-login-choice')">Avanti</button>
  </div>
  <div style="height:40px"></div>
</div>

<!-- ═══ LOGIN CHOICE ═══ -->
<div class="screen" id="s-login-choice">
  <div class="sb"><span class="sb-t">9:41</span><span class="sb-r"></span></div>
  <div class="center-col">
    <img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAZkAAACnCAYAAADDoiGnAAAACXBIWXMAAAsTAAALEwEAmpwYAAAAAXNSR0IArs4c6QAAAARnQU1BAACxjwv8YQUAAAAOdEVYdFNvZnR3YXJlAEZpZ21hnrGWYwAAml5JREFUeAHt/XuQXNl5Hwh+59x782bWu4AqAIUGuiEQBCmALZKC1BSplhqjdawpL3cndlbgeP7aoULmhtcjT3hjNBPWrAOFnfE6pJF2YqRdbixty3bEzmjdkHcidhVDz4TtQcttyqIHEqkmIBJdaqIb1Y1HFeqZVZl5H+fM9/vOOZm3qoFmdxbILgD36764N+8rb9465/zO73sS1VJLLbXUUksttdRSSy211FJLLbXUUksttdRSSy211FJLLbXUUksttdRSSy211FJLLbXUUksttdRSSy211FJLLbXUUksttdRSSy211FJLLbXUUksttdRSSy211FJLLbXUUksttdRSSy211FJLLbXUUksttdRSSy211FJLLbXUUksttdRSSy211FJLLbXUUksttfxQxFq7+7PilSzYrhwP+2up5aHi2w+k336q+yrLu9peLbXU8phLBUCCeDAZdP6LFy/qcF5YX7xImnYODDXg1CLyoDZVaS87FrQtvmL3/v51VEsttTz2oh6waD8o7FgwIFy4cCFyA8ODB41w08pMtZanS/qTELQBtJXQXsJ2+LyzLV3st6dwHQ0mMXVb2sdS/3FqeZhUAYHm55W6fv3CjvaytLS04/Ps7KwN+7B9+fJly4OBP3qJLl0iUBpLO9tdrf94egQAYbktATTo+vXrD2xPL730Er3yyiv99ZUrV6SNMOjQmTNn7CVuSGhW8/OMLkpV21Pdlvah1CBTyw4Js0LuvP19DBQqDAhhINjc3FTnzp2j1dVVNT39hl1dPdm/AJ+xvnFjXNYYLPh66wcIu/PrME6oenB4skWFuQUDhcbkAx/Onz8vbeb06dO8vkpoQ9PT03ZublXdvu3akNv3hg1tCZMXrP09+u0GE6G6He1PqUGmlt0ibYJnirIO7KUKLidPOkBpt9vq1CmihYXX6YUXXlQrK3elky8suBuNjY1ZDBo3btzYMUBUwaYeHJ58wUQCTBjbg/Z0WZ0+/WV19epVOnTokO50OrL/+edb/bawudlRd++6z2hLWKM94Rpugwaf0ZYcS4bh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" alt="DOT" style="height:80px;margin-bottom:40px;display:block">
    <div style="font-size:22px;font-weight:800;color:var(--navy);margin-bottom:6px;letter-spacing:-.02em">Hai già un profilo?</div>
    <div style="font-size:14px;color:var(--muted);margin-bottom:36px">Accedi o crea il tuo archivio.</div>
    <button class="btn btn-primary" style="margin-bottom:14px" onclick="go('s-login')">Accedi</button>
    <button class="btn btn-ghost" onclick="go('s-register')">Registrati</button>
  </div>
  <div style="height:40px"></div>
</div>

<!-- ═══ LOGIN ═══ -->
<div class="screen" id="s-login">
  <div class="sb"><span class="sb-t">9:41</span><span class="sb-r"></span></div>
  <div class="ai-hdr" style="padding-top:0"><button class="ai-back" aria-label="Indietro" onclick="goBack()">‹</button></div>
  <div class="center-col" style="justify-content:flex-start;padding-top:10px">
    <img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAZkAAACnCAYAAADDoiGnAAAACXBIWXMAAAsTAAALEwEAmpwYAAAAAXNSR0IArs4c6QAAAARnQU1BAACxjwv8YQUAAAAOdEVYdFNvZnR3YXJlAEZpZ21hnrGWYwAAml5JREFUeAHt/XuQXNl5Hwh+59x782bWu4AqAIUGuiEQBCmALZKC1BSplhqjdawpL3cndlbgeP7aoULmhtcjT3hjNBPWrAOFnfE6pJF2YqRdbixty3bEzmjdkHcidhVDz4TtQcttyqIHEqkmIBJdaqIb1Y1HFeqZVZl5H+fM9/vOOZm3qoFmdxbILgD36764N+8rb9465/zO73sS1VJLLbXUUksttdRSSy211FJLLbXUUksttdRSSy211FJLLbXUUksttdRSSy211FJLLbXUUksttdRSSy211FJLLbXUUksttdRSSy211FJLLbXUUksttdRSSy211FJLLbXUUksttdRSSy211FJLLbXUUksttdRSSy211FJLLbXUUksttdRSSy211FJLLbXUUksttfxQxFq7+7PilSzYrhwP+2up5aHi2w+k336q+yrLu9peLbXU8phLBUCCeDAZdP6LFy/qcF5YX7xImnYODDXg1CLyoDZVaS87FrQtvmL3/v51VEsttTz2oh6waD8o7FgwIFy4cCFyA8ODB41w08pMtZanS/qTELQBtJXQXsJ2+LyzLV3st6dwHQ0mMXVb2sdS/3FqeZhUAYHm55W6fv3CjvaytLS04/Ps7KwN+7B9+fJly4OBP3qJLl0iUBpLO9tdrf94egQAYbktATTo+vXrD2xPL730Er3yyiv99ZUrV6SNMOjQmTNn7CVuSGhW8/OMLkpV21Pdlvah1CBTyw4Js0LuvP19DBQqDAhhINjc3FTnzp2j1dVVNT39hl1dPdm/AJ+xvnFjXNYYLPh66wcIu/PrME6oenB4skWFuQUDhcbkAx/Onz8vbeb06dO8vkpoQ9PT03ZublXdvu3akNv3hg1tCZMXrP09+u0GE6G6He1PqUGmlt0ibYJnirIO7KUKLidPOkBpt9vq1CmihYXX6YUXXlQrK3elky8suBuNjY1ZDBo3btzYMUBUwaYeHJ58wUQCTBjbg/Z0WZ0+/WV19epVOnTokO50OrL/+edb/bawudlRd++6z2hLWKM94Rpugwaf0ZYcS4bh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" alt="DOT" style="height:70px;margin-bottom:28px;display:block">
    <button class="social-btn" onclick="go('s-home')">Continua con Google</button>
    <button class="social-btn" onclick="go('s-home')">Continua con Apple</button>
    <div class="divider"><span>oppure</span></div>
    <input class="input" placeholder="Email" type="email">
    <input class="input" placeholder="Password" type="password">
    <button class="btn btn-primary" style="margin-top:6px" onclick="go('s-home')">Accedi</button>
  </div>
</div>

<!-- ═══ REGISTER ═══ -->
<div class="screen" id="s-register">
  <div class="sb"><span class="sb-t">9:41</span><span class="sb-r"></span></div>
  <div class="ai-hdr" style="padding-top:0"><button class="ai-back" aria-label="Indietro" onclick="goBack()">‹</button></div>
  <div class="center-col" style="justify-content:flex-start;padding-top:10px">
    <img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAZkAAACnCAYAAADDoiGnAAAACXBIWXMAAAsTAAALEwEAmpwYAAAAAXNSR0IArs4c6QAAAARnQU1BAACxjwv8YQUAAAAOdEVYdFNvZnR3YXJlAEZpZ21hnrGWYwAAml5JREFUeAHt/XuQXNl5Hwh+59x782bWu4AqAIUGuiEQBCmALZKC1BSplhqjdawpL3cndlbgeP7aoULmhtcjT3hjNBPWrAOFnfE6pJF2YqRdbixty3bEzmjdkHcidhVDz4TtQcttyqIHEqkmIBJdaqIb1Y1HFeqZVZl5H+fM9/vOOZm3qoFmdxbILgD36764N+8rb9465/zO73sS1VJLLbXUUksttdRSSy211FJLLbXUUksttdRSSy211FJLLbXUUksttdRSSy211FJLLbXUUksttdRSSy211FJLLbXUUksttdRSSy211FJLLbXUUksttdRSSy211FJLLbXUUksttdRSSy211FJLLbXUUksttdRSSy211FJLLbXUUksttdRSSy211FJLLbXUUksttfxQxFq7+7PilSzYrhwP+2up5aHi2w+k336q+yrLu9peLbXU8phLBUCCeDAZdP6LFy/qcF5YX7xImnYODDXg1CLyoDZVaS87FrQtvmL3/v51VEsttTz2oh6waD8o7FgwIFy4cCFyA8ODB41w08pMtZanS/qTELQBtJXQXsJ2+LyzLV3st6dwHQ0mMXVb2sdS/3FqeZhUAYHm55W6fv3CjvaytLS04/Ps7KwN+7B9+fJly4OBP3qJLl0iUBpLO9tdrf94egQAYbktATTo+vXrD2xPL730Er3yyiv99ZUrV6SNMOjQmTNn7CVuSGhW8/OMLkpV21Pdlvah1CBTyw4Js0LuvP19DBQqDAhhINjc3FTnzp2j1dVVNT39hl1dPdm/AJ+xvnFjXNYYLPh66wcIu/PrME6oenB4skWFuQUDhcbkAx/Onz8vbeb06dO8vkpoQ9PT03ZublXdvu3akNv3hg1tCZMXrP09+u0GE6G6He1PqUGmlt0ibYJnirIO7KUKLidPOkBpt9vq1CmihYXX6YUXXlQrK3elky8suBuNjY1ZDBo3btzYMUBUwaYeHJ58wUQCTBjbg/Z0WZ0+/WV19epVOnTokO50OrL/+edb/bawudlRd++6z2hLWKM94Rpugwaf0ZYcS4bh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" alt="DOT" style="height:70px;margin-bottom:28px;display:block">
    <button class="social-btn" onclick="go('s-ob1')">Continua con Google</button>
    <button class="social-btn" onclick="go('s-ob1')">Continua con Apple</button>
    <div class="divider"><span>oppure</span></div>
    <input class="input" placeholder="Email">
    <input class="input" placeholder="Password">
    <button class="btn btn-primary" style="margin-top:6px" onclick="go('s-ob1')">Crea account</button>
  </div>
</div>

<!-- ═══ ONBOARDING 1 ═══ -->
<div class="screen" id="s-ob1">
  <div class="sb"><span class="sb-t">9:41</span><span class="sb-r"></span></div>
  <div class="ob-dots"><div class="ob-dot on"></div><div class="ob-dot"></div><div class="ob-dot"></div></div>
  <div class="center-col">
    <div class="wave-mark" style="width:120px;height:120px;margin-bottom:36px;box-shadow:var(--sh-btn-strong)"></div>
    <div style="font-size:26px;font-weight:800;color:var(--navy);letter-spacing:-.02em;margin-bottom:12px">Un solo archivio<br>per tutto te stesso</div>
    <div style="font-size:15px;color:var(--navy-soft);line-height:1.55">I tuoi dati vengono raccolti e organizzati nel tempo, per una visione più completa del tuo stato.</div>
  </div>
  <div class="pad" style="padding-bottom:36px"><button class="btn btn-primary" onclick="go('s-ob2')">Avanti</button></div>
</div>

<!-- ═══ ONBOARDING 2 ═══ -->
<div class="screen" id="s-ob2">
  <div class="sb"><span class="sb-t">9:41</span><span class="sb-r"></span></div>
  <div class="ob-dots"><div class="ob-dot"></div><div class="ob-dot on"></div><div class="ob-dot"></div></div>
  <div class="center-col">
    <div style="width:120px;height:120px;border-radius:50%;background:var(--orange-soft);display:flex;align-items:center;justify-content:center;margin-bottom:36px">
      <svg width="56" height="56" viewBox="0 0 24 24" fill="none" stroke="var(--orange)" stroke-width="1.5"><rect x="5" y="11" width="14" height="10" rx="2"/><path d="M8 11V7a4 4 0 018 0v4"/></svg>
    </div>
    <div style="font-size:26px;font-weight:800;color:var(--navy);letter-spacing:-.02em;margin-bottom:12px">I tuoi dati<br>restano tuoi</div>
    <div style="font-size:15px;color:var(--navy-soft);line-height:1.55">Tutto è cifrato e protetto. Solo tu decidi cosa condividere e con chi. L'archivio risponde a te.</div>
  </div>
  <div class="pad" style="padding-bottom:36px"><button class="btn btn-primary" onclick="go('s-ob3')">Avanti</button></div>
</div>

<!-- ═══ ONBOARDING 3 ═══ -->
<div class="screen" id="s-ob3">
  <div class="sb"><span class="sb-t">9:41</span><span class="sb-r"></span></div>
  <div class="ob-dots"><div class="ob-dot"></div><div class="ob-dot"></div><div class="ob-dot on"></div></div>
  <div class="center-col">
    <div style="width:120px;height:120px;border-radius:50%;background:var(--orange-soft);display:flex;align-items:center;justify-content:center;margin-bottom:36px">
      <svg width="56" height="56" viewBox="0 0 24 24" fill="none" stroke="var(--orange)" stroke-width="1.5"><circle cx="12" cy="12" r="3"/><path d="M12 5a7 7 0 00-7 7"/><path d="M12 2a10 10 0 00-10 10"/></svg>
    </div>
    <div style="font-size:26px;font-weight:800;color:var(--navy);letter-spacing:-.02em;margin-bottom:12px">Un archivio<br>che ti osserva</div>
    <div style="font-size:15px;color:var(--navy-soft);line-height:1.55">DOT legge i tuoi dati e te li restituisce con calma, collegando ciò che vivi a ciò che misuri.</div>
  </div>
  <div class="pad" style="padding-bottom:36px"><button class="btn btn-primary" onclick="go('s-cal-age')">Inizia</button></div>
</div>

<!-- ═══ PROFILAZIONE — progress bar in alto ═══ -->

<!-- STEP 1: ETÀ -->
<div class="screen" id="s-cal-age">
  <div class="sb"><span class="sb-t">9:41</span><span class="sb-r"></span></div>
  <div class="ai-hdr" style="padding-bottom:8px"><button class="ai-back" aria-label="Indietro" onclick="goBack()">‹</button>
    <div class="pbar"><div class="pbar-fill" style="width:10%"></div></div></div>
  <div style="padding:0 24px 4px"><div class="eyebrow">Chi sei · 1 di 10</div><div class="scr-title" style="margin-top:6px">Quanti anni hai?</div></div>
  <div class="drum-area">
    <div class="drum-sel"></div>
    <div class="drum-wrap"><div class="drum" id="drum-age" onscroll="onDrum(this)"></div><div class="drum-unit">anni</div></div>
  </div>
  <div class="pad" style="padding-bottom:32px"><button class="btn btn-primary" onclick="go('s-cal-weight')">Continua</button></div>
</div>

<!-- STEP 2: PESO -->
<div class="screen" id="s-cal-weight">
  <div class="sb"><span class="sb-t">9:41</span><span class="sb-r"></span></div>
  <div class="ai-hdr" style="padding-bottom:8px"><button class="ai-back" aria-label="Indietro" onclick="goBack()">‹</button>
    <div class="pbar"><div class="pbar-fill" style="width:20%"></div></div></div>
  <div style="padding:0 24px 4px"><div class="eyebrow">Chi sei · 2 di 10</div><div class="scr-title" style="margin-top:6px">Il tuo peso</div></div>
  <div class="drum-area">
    <div class="drum-sel"></div>
    <div class="drum-wrap"><div class="drum" id="drum-weight" onscroll="onDrum(this)"></div><div class="drum-unit">kg</div></div>
  </div>
  <div class="pad" style="padding-bottom:32px"><button class="btn btn-primary" onclick="go('s-cal-height')">Continua</button></div>
</div>

<!-- STEP 3: ALTEZZA -->
<div class="screen" id="s-cal-height">
  <div class="sb"><span class="sb-t">9:41</span><span class="sb-r"></span></div>
  <div class="ai-hdr" style="padding-bottom:8px"><button class="ai-back" aria-label="Indietro" onclick="goBack()">‹</button>
    <div class="pbar"><div class="pbar-fill" style="width:30%"></div></div></div>
  <div style="padding:0 24px 4px"><div class="eyebrow">Chi sei · 3 di 10</div><div class="scr-title" style="margin-top:6px">La tua altezza</div></div>
  <div class="drum-area">
    <div class="drum-sel"></div>
    <div class="drum-wrap"><div class="drum" id="drum-height" onscroll="onDrum(this)"></div><div class="drum-unit">cm</div></div>
  </div>
  <div class="pad" style="padding-bottom:32px"><button class="btn btn-primary" onclick="go('s-q-sport')">Continua</button></div>
</div>

<!-- STEP 4: ATTIVITÀ PRATICATE (multi) -->
<div class="screen" id="s-q-sport">
  <div class="sb"><span class="sb-t">9:41</span><span class="sb-r"></span></div>
  <div class="ai-hdr" style="padding-bottom:8px"><button class="ai-back" aria-label="Indietro" onclick="goBack()">‹</button>
    <div class="pbar"><div class="pbar-fill" style="width:40%"></div></div></div>
  <div style="padding:0 24px 18px"><div class="eyebrow">Come ti muovi · 4 di 10</div><div class="scr-title" style="margin-top:6px;font-size:28px">Attività praticate</div>
    <div class="scr-sub" style="margin-top:6px">Seleziona tutte quelle che ti riguardano.</div></div>
  <div class="body" style="padding-bottom:100px">
    <div class="sel-list">
      <div class="sel-item" onclick="multiSel(this)">Sport individuale<div class="ck"></div></div>
      <div class="sel-item" onclick="multiSel(this)">Sport di squadra<div class="ck"></div></div>
      <div class="sel-item" onclick="multiSel(this)">Outdoor &amp; resistenza<div class="ck"></div></div>
      <div class="sel-item" onclick="multiSel(this)">Forza &amp; palestra<div class="ck"></div></div>
      <div class="sel-item" onclick="multiSel(this)">Mobilità &amp; recupero<div class="ck"></div></div>
      <div class="sel-item" onclick="multiSel(this)">Altro<div class="ck"></div></div>
    </div>
  </div>
  <div style="position:absolute;bottom:0;left:0;right:0;padding:14px 24px 30px;background:var(--bg);border-top:1.5px solid var(--line)">
    <button class="btn btn-primary" onclick="go('s-q-level')">Continua</button>
  </div>
</div>

<!-- STEP 5: LIVELLO DI PRATICA (single) -->
<div class="screen" id="s-q-level">
  <div class="sb"><span class="sb-t">9:41</span><span class="sb-r"></span></div>
  <div class="ai-hdr" style="padding-bottom:8px"><button class="ai-back" aria-label="Indietro" onclick="goBack()">‹</button>
    <div class="pbar"><div class="pbar-fill" style="width:50%"></div></div></div>
  <div style="padding:0 24px 18px"><div class="eyebrow">Come ti muovi · 5 di 10</div><div class="scr-title" style="margin-top:6px;font-size:28px">Livello di pratica</div></div>
  <div class="body" style="padding-bottom:100px">
    <div class="sel-list">
      <div class="sel-item" onclick="singleSel(this)">Saltuario<div class="ck"></div></div>
      <div class="sel-item" onclick="singleSel(this)">Amatoriale<div class="ck"></div></div>
      <div class="sel-item" onclick="singleSel(this)">Agonistico<div class="ck"></div></div>
      <div class="sel-item" onclick="singleSel(this)">Professionista<div class="ck"></div></div>
    </div>
  </div>
  <div style="position:absolute;bottom:0;left:0;right:0;padding:14px 24px 30px;background:var(--bg);border-top:1.5px solid var(--line)">
    <button class="btn btn-primary" onclick="go('s-q-freq')">Continua</button>
  </div>
</div>

<!-- STEP 6: FREQUENZA (single) -->
<div class="screen" id="s-q-freq">
  <div class="sb"><span class="sb-t">9:41</span><span class="sb-r"></span></div>
  <div class="ai-hdr" style="padding-bottom:8px"><button class="ai-back" aria-label="Indietro" onclick="goBack()">‹</button>
    <div class="pbar"><div class="pbar-fill" style="width:60%"></div></div></div>
  <div style="padding:0 24px 18px"><div class="eyebrow">Come ti muovi · 6 di 10</div><div class="scr-title" style="margin-top:6px;font-size:28px">Quanto ti alleni?</div></div>
  <div class="body" style="padding-bottom:100px">
    <div class="sel-list">
      <div class="sel-item" onclick="singleSel(this)">1–2 volte a settimana<div class="ck"></div></div>
      <div class="sel-item" onclick="singleSel(this)">3–4 volte a settimana<div class="ck"></div></div>
      <div class="sel-item" onclick="singleSel(this)">5 o più volte a settimana<div class="ck"></div></div>
      <div class="sel-item" onclick="singleSel(this)">Ogni giorno<div class="ck"></div></div>
    </div>
  </div>
  <div style="position:absolute;bottom:0;left:0;right:0;padding:14px 24px 30px;background:var(--bg);border-top:1.5px solid var(--line)">
    <button class="btn btn-primary" onclick="go('s-q-goal')">Continua</button>
  </div>
</div>

<!-- STEP 7: OBIETTIVO (multi) -->
<div class="screen" id="s-q-goal">
  <div class="sb"><span class="sb-t">9:41</span><span class="sb-r"></span></div>
  <div class="ai-hdr" style="padding-bottom:8px"><button class="ai-back" aria-label="Indietro" onclick="goBack()">‹</button>
    <div class="pbar"><div class="pbar-fill" style="width:70%"></div></div></div>
  <div style="padding:0 24px 18px"><div class="eyebrow">Cosa cerchi · 7 di 10</div><div class="scr-title" style="margin-top:6px;font-size:28px">Il tuo obiettivo</div>
    <div class="scr-sub" style="margin-top:6px">Cosa vuoi che DOT tenga d'occhio per te.</div></div>
  <div class="body" style="padding-bottom:100px">
    <div class="sel-list">
      <div class="sel-item" onclick="multiSel(this)">Performance<div class="ck"></div></div>
      <div class="sel-item" onclick="multiSel(this)">Benessere generale<div class="ck"></div></div>
      <div class="sel-item" onclick="multiSel(this)">Recupero infortuni<div class="ck"></div></div>
      <div class="sel-item" onclick="multiSel(this)">Monitoraggio salute<div class="ck"></div></div>
      <div class="sel-item" onclick="multiSel(this)">Prevenzione<div class="ck"></div></div>
      <div class="sel-item" onclick="multiSel(this)">Equilibrio mente-corpo<div class="ck"></div></div>
    </div>
  </div>
  <div style="position:absolute;bottom:0;left:0;right:0;padding:14px 24px 30px;background:var(--bg);border-top:1.5px solid var(--line)">
    <button class="btn btn-primary" onclick="go('s-complete-form')">Continua</button>
  </div>
</div>

<!-- STEP 8: COMPLETA IL PROFILO (form anagrafica) -->
<div class="screen" id="s-complete-form">
  <div class="sb"><span class="sb-t">9:41</span><span class="sb-r"></span></div>
  <div class="ai-hdr" style="padding-bottom:8px"><button class="ai-back" aria-label="Indietro" onclick="goBack()">‹</button>
    <div class="pbar"><div class="pbar-fill" style="width:80%"></div></div></div>
  <div style="padding:0 24px 8px"><div class="eyebrow">Ci siamo quasi · 8 di 10</div>
    <div class="scr-title" style="margin-top:6px;font-size:28px">Completa il profilo</div>
    <div class="scr-sub" style="margin-top:6px">Inserisci queste ultime informazioni.</div></div>
  <div class="body" style="padding:14px 24px 100px">
    <div style="display:flex;justify-content:center;margin-bottom:22px">
      <div style="width:84px;height:84px;border-radius:50%;background:var(--ice-deep);border:1.5px dashed var(--line-orange);display:flex;align-items:center;justify-content:center;cursor:pointer">
        <i class="ti" style="font-size:0"></i>
        <svg width="30" height="30" viewBox="0 0 24 24" fill="none" stroke="var(--orange)" stroke-width="1.5"><circle cx="12" cy="8" r="4"/><path d="M4 20c0-4 4-6 8-6s8 2 8 6" stroke-linecap="round"/></svg>
      </div>
    </div>
    <div class="prof-sec-l" style="padding:0;margin:0 0 8px">Nome</div>
    <input class="input" placeholder="Giulia" value="Giulia">
    <div class="prof-sec-l" style="padding:0;margin:6px 0 8px">Cognome</div>
    <input class="input" placeholder="Ferretti" value="Ferretti">
    <div class="prof-sec-l" style="padding:0;margin:6px 0 8px">Email</div>
    <input class="input" type="email" placeholder="giulia.ferretti@example.com" value="giulia.ferretti@example.com">
    <div class="prof-sec-l" style="padding:0;margin:6px 0 8px">Password</div>
    <input class="input" type="password" placeholder="••••••••" value="dotarchivio">
  </div>
  <div style="position:absolute;bottom:0;left:0;right:0;padding:14px 24px 30px;background:var(--bg);border-top:1.5px solid var(--line)">
    <button class="btn btn-primary" onclick="go('s-q-occupation')">Continua</button>
  </div>
</div>

<!-- STEP 9: STUDENTE / LAVORATORE (single) -->
<div class="screen" id="s-q-occupation">
  <div class="sb"><span class="sb-t">9:41</span><span class="sb-r"></span></div>
  <div class="ai-hdr" style="padding-bottom:8px"><button class="ai-back" aria-label="Indietro" onclick="goBack()">‹</button>
    <div class="pbar"><div class="pbar-fill" style="width:90%"></div></div></div>
  <div style="padding:0 24px 18px"><div class="eyebrow">Le tue giornate · 9 di 10</div><div class="scr-title" style="margin-top:6px;font-size:28px">Come passi le giornate?</div>
    <div class="scr-sub" style="margin-top:6px">Aiuta DOT a leggere i tuoi ritmi.</div></div>
  <div class="body" style="padding-bottom:100px">
    <div class="sel-list">
      <div class="sel-item" onclick="singleSel(this)">Studente<div class="ck"></div></div>
      <div class="sel-item" onclick="singleSel(this)">Lavoratore<div class="ck"></div></div>
      <div class="sel-item" onclick="singleSel(this)">Studente e lavoratore<div class="ck"></div></div>
      <div class="sel-item" onclick="singleSel(this)">Altro<div class="ck"></div></div>
    </div>
  </div>
  <div style="position:absolute;bottom:0;left:0;right:0;padding:14px 24px 30px;background:var(--bg);border-top:1.5px solid var(--line)">
    <button class="btn btn-primary" onclick="go('s-raccolta')">Continua</button>
  </div>
</div>

<!-- STEP 9: APP / FONTI -->
<div class="screen" id="s-raccolta">
  <div class="sb"><span class="sb-t">9:41</span><span class="sb-r"></span></div>
  <div class="ai-hdr" style="padding-bottom:8px"><button class="ai-back" aria-label="Indietro" onclick="goBack()">‹</button>
    <div class="pbar"><div class="pbar-fill" style="width:100%"></div></div></div>
  <div style="padding:0 24px 14px;flex-shrink:0">
    <div class="eyebrow">Le tue fonti · 10 di 10</div>
    <div class="scr-title" style="font-size:28px;margin-top:6px;margin-bottom:6px">Quali app aggiungi?</div>
    <div class="scr-sub">Connetti solo ciò che vuoi. Sono i trigger del tuo archivio.</div>
  </div>
  <div class="body" style="padding-bottom:100px">
    <div class="prof-sec-l">App salute &amp; fitness</div>
    <div class="prof-card">
      <div class="prof-row" onclick="toggleSrc(this)"><div class="pri-ico">♥</div><div><div class="pri-name">Apple Health</div><div class="pri-sub">Battiti · Passi · Sonno</div></div><div class="pri-badge on">Connesso</div></div>
      <div class="prof-row" onclick="toggleSrc(this)"><div class="pri-ico">⚡</div><div><div class="pri-name">Strava</div><div class="pri-sub">Corsa · Ciclismo · Nuoto</div></div><div class="pri-badge on">Connesso</div></div>
      <div class="prof-row" onclick="toggleSrc(this)"><div class="pri-ico">🥗</div><div><div class="pri-name">Yuka</div><div class="pri-sub">Qualità alimentare</div></div><div class="pri-badge off">Collega</div></div>
      <div class="prof-row" onclick="toggleSrc(this)"><div class="pri-ico">🏃</div><div><div class="pri-name">Nike Training</div><div class="pri-sub">Workout · Home fitness</div></div><div class="pri-badge off">Collega</div></div>
    </div>
    <div class="prof-sec-l">Wearable</div>
    <div class="prof-card">
      <div class="prof-row" onclick="toggleSrc(this)"><div class="pri-ico">⌚</div><div><div class="pri-name">Apple Watch</div><div class="pri-sub">HRV · SpO₂ · Sonno</div></div><div class="pri-badge on">Connesso</div></div>
    </div>
    <div class="prof-sec-l">Documenti medici</div>
    <div class="prof-card">
      <div class="prof-row" onclick="toggleSrc(this)"><div class="pri-ico">📄</div><div><div class="pri-name">Fascicolo Sanitario</div><div class="pri-sub">Referti · Esami · Emilia-Romagna</div></div><div class="pri-badge off">Collega</div></div>
    </div>
  </div>
  <div style="position:absolute;bottom:0;left:0;right:0;padding:14px 24px 30px;background:var(--bg);border-top:1.5px solid var(--line)">
    <button class="btn btn-primary" onclick="go('s-complete')">Completa il profilo</button>
  </div>
</div>

<!-- PROFILO COMPLETATO -->
<div class="screen" id="s-complete">
  <div class="sb"><span class="sb-t">9:41</span><span class="sb-r"></span></div>
  <div class="center-col">
    <div style="width:96px;height:96px;border-radius:50%;background:var(--orange);display:flex;align-items:center;justify-content:center;margin-bottom:32px;box-shadow:var(--sh-btn-strong)">
      <svg width="48" height="48" viewBox="0 0 24 24" fill="none" stroke="#fff" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><path d="M5 13l4 4L19 7"/></svg>
    </div>
    <div style="font-size:26px;font-weight:800;color:var(--navy);letter-spacing:-.02em;margin-bottom:12px">Hai completato<br>il tuo profilo!</div>
    <div style="font-size:15px;color:var(--navy-soft);line-height:1.55">Il tuo Digital Phenotype è pronto. DOT comincia a leggere i tuoi trigger per restituirti la prima osservazione.</div>
  </div>
  <div class="pad" style="padding-bottom:36px"><button class="btn btn-primary" onclick="go('s-home')">Iniziamo</button></div>
</div>


<!-- ═══ HOME ═══ -->
<div class="screen" id="s-home">
  <div class="sb"><span class="sb-t">9:41</span><span class="sb-r"></span></div>
  <div class="hdr-row">
    <div>
      <div class="eyebrow" style="margin-bottom:8px">Osservazione al log-in</div>
      <div class="obs-phrase" id="obs-phrase">Buongiorno, Giulia.</div>
    </div>
    <div class="avatar" role="button" aria-label="Apri profilo di Giulia" onclick="switchTab('profile')">G</div>
  </div>
  <div class="chips-row" id="home-chips">
    <div class="chip on" data-f="tutti" onclick="filterHome(this)">Tutti</div>
    <div class="chip" data-f="attivita" onclick="filterHome(this)">Attività</div>
    <div class="chip" data-f="sonno" onclick="filterHome(this)">Sonno</div>
    <div class="chip" data-f="benessere" onclick="filterHome(this)">Benessere</div>
  </div>
  <div class="body" style="padding-bottom:108px;position:relative">
    <div class="home-bg" aria-hidden="true"><canvas id="home-node-cloud"></canvas></div>
    <div class="home-stack-wrap">
      <div class="stack-hint">Le insight prodotte dal tuo DOT · tocca per approfondire</div>
      <div class="stack" id="home-stack"></div>
    </div>
  </div>
  <div class="bnav">
    <svg class="bnav-net" viewBox="0 0 402 48" preserveAspectRatio="none">
      <line x1="70" y1="24" x2="201" y2="24"/><line x1="201" y1="24" x2="332" y2="24"/>
      <line x1="70" y1="24" x2="140" y2="12"/><line x1="140" y1="12" x2="201" y2="24"/>
      <line x1="201" y1="24" x2="262" y2="36"/><line x1="262" y1="36" x2="332" y2="24"/>
      <circle class="node" cx="140" cy="12" r="2"/><circle class="node" cx="262" cy="36" r="2"/>
      <circle class="node" cx="105" cy="24" r="1.6"/><circle class="node" cx="296" cy="24" r="1.6"/>
      <circle class="flux" cx="332" cy="24" r="3.2"/>
      <circle class="flux" cx="332" cy="24" r="2" style="animation-delay:.15s"/>
    </svg>
    <div class="bni on" onclick="switchTab('home')">
      <svg viewBox="0 0 24 24"><path d="M3 11l9-8 9 8M5 9.5V20a1 1 0 001 1h4v-6h4v6h4a1 1 0 001-1V9.5" stroke-linecap="round" stroke-linejoin="round"/></svg>
      <span class="bni-l">Home</span>
    </div>
    <div class="dot-btn-w" onclick="openOverlay()">
      <div class="dot-btn"><svg viewBox="0 0 24 24"><path d="M12 5v14M5 12h14"/></svg></div>
      <div class="dot-btn-l">Dot</div>
    </div>
    <div class="bni" onclick="switchTab('vault')">
      <svg viewBox="0 0 24 24"><rect x="5" y="3" width="14" height="18" rx="2.5"/><path d="M9 8h6M9 12h6M9 16h4" stroke-linecap="round"/></svg>
      <span class="bni-l">Memoria</span>
    </div>
  </div>
</div>

<!-- ═══ MEMORIA — rete nodale: Trigger → DOT → Insight ═══ -->
<div class="screen" id="s-vault">
  <div class="sb"><span class="sb-t">9:41</span><span class="sb-r"></span></div>
  <div class="hdr-row" style="padding-bottom:8px">
    <div>
      <div class="eyebrow" style="margin-bottom:6px">Il motore del tuo Phenotype</div>
      <div class="scr-title">Memoria</div>
    </div>
    <div class="avatar" role="button" aria-label="Apri profilo di Giulia" onclick="switchTab('profile')">G</div>
  </div>

  <!-- ═ PRIMO TERZO: rete nodale ridotta + shortcut app trigger ═ -->
  <div class="net-third">
    <canvas id="net-canvas"></canvas>
    <div class="net-third-apps" aria-label="App che inviano trigger">
      <button class="net-app" data-app="strava" style="--c:#D98324" onclick="pingTrigger(this)" aria-label="Strava"><i class="ti ti-run"></i></button>
      <button class="net-app" data-app="health" style="--c:#C0436B" onclick="pingTrigger(this)" aria-label="Apple Health"><i class="ti ti-heart"></i></button>
      <button class="net-app" data-app="watch" style="--c:#2B2118" onclick="pingTrigger(this)" aria-label="Apple Watch"><i class="ti ti-device-watch"></i></button>
      <button class="net-app" data-app="yuka" style="--c:#5B8C3E" onclick="pingTrigger(this)" aria-label="Yuka"><i class="ti ti-leaf"></i></button>
      <button class="net-app empty" onclick="go('s-raccolta')" aria-label="Collega un'app"><i class="ti ti-plus"></i></button>
    </div>
    <div class="net-third-reveal" id="net-reveal"><span class="nr-default">Le tue app inviano i <b>trigger</b> al DOT · toccane una per vedere cosa raccoglie</span></div>
  </div>

  <!-- ═ DUE TERZI: nota + storico chat ═ -->
  <div class="body vault-lower">
    <button class="note-cta" onclick="go('s-aggiungi')">
      <span class="note-cta-ic"><i class="ti ti-pencil-plus"></i></span>
      <span class="note-cta-tx"><b>Lascia una nota</b><i>Aggiungila al flusso con tempo e contesto</i></span>
      <i class="ti ti-plus note-cta-plus"></i>
    </button>

    <div class="vault-sec-h">
      <span class="sec-l" style="font-size:18px;font-weight:800;letter-spacing:-.02em">Storico conversazioni</span>
      <button class="sec-link" onclick="openOverlay()">Nuova chat</button>
    </div>
    <div class="chat-history">
      <button class="chist" onclick="openOverlay()">
        <span class="chist-ic"><i class="ti ti-message-circle"></i></span>
        <span class="chist-tx"><b>Mi alleno oggi?</b><i>HRV sotto media · recupero attivo consigliato</i></span>
        <span class="chist-t">Oggi</span>
      </button>
      <button class="chist" onclick="openOverlay()">
        <span class="chist-ic"><i class="ti ti-message-circle"></i></span>
        <span class="chist-tx"><b>Come sto dormendo?</b><i>Sonno profondo basso da 3 notti</i></span>
        <span class="chist-t">Ieri</span>
      </button>
      <button class="chist" onclick="openOverlay()">
        <span class="chist-ic"><i class="ti ti-message-circle"></i></span>
        <span class="chist-tx"><b>Il referto è collegato agli allenamenti?</b><i>Nessun parametro limita il carico</i></span>
        <span class="chist-t">Lun</span>
      </button>
      <button class="chist" onclick="openOverlay()">
        <span class="chist-ic"><i class="ti ti-message-circle"></i></span>
        <span class="chist-tx"><b>Cosa mangio stasera?</b><i>Piatto proteico semplice · 15 min</i></span>
        <span class="chist-t">Dom</span>
      </button>
    </div>
  </div>

  <div class="bnav">
    <svg class="bnav-net" viewBox="0 0 402 48" preserveAspectRatio="none">
      <line x1="70" y1="24" x2="201" y2="24"/><line x1="201" y1="24" x2="332" y2="24"/>
      <line x1="70" y1="24" x2="140" y2="12"/><line x1="140" y1="12" x2="201" y2="24"/>
      <line x1="201" y1="24" x2="262" y2="36"/><line x1="262" y1="36" x2="332" y2="24"/>
      <circle class="node" cx="140" cy="12" r="2"/><circle class="node" cx="262" cy="36" r="2"/>
      <circle class="node" cx="105" cy="24" r="1.6"/><circle class="node" cx="296" cy="24" r="1.6"/>
      <circle class="flux" cx="332" cy="24" r="3.2"/>
      <circle class="flux" cx="332" cy="24" r="2" style="animation-delay:.15s"/>
    </svg>
    <div class="bni" onclick="switchTab('home')">
      <svg viewBox="0 0 24 24"><path d="M3 11l9-8 9 8M5 9.5V20a1 1 0 001 1h4v-6h4v6h4a1 1 0 001-1V9.5" stroke-linecap="round" stroke-linejoin="round"/></svg>
      <span class="bni-l">Home</span>
    </div>
    <div class="dot-btn-w" onclick="openOverlay()">
      <div class="dot-btn"><svg viewBox="0 0 24 24"><path d="M12 5v14M5 12h14"/></svg></div>
      <div class="dot-btn-l">Dot</div>
    </div>
    <div class="bni on" onclick="switchTab('vault')">
      <svg viewBox="0 0 24 24"><rect x="5" y="3" width="14" height="18" rx="2.5"/><path d="M9 8h6M9 12h6M9 16h4" stroke-linecap="round"/></svg>
      <span class="bni-l">Memoria</span>
    </div>
  </div>
</div>


<!-- ═══ AGGIUNGI REGISTRAZIONE ═══ -->
<div class="screen" id="s-aggiungi">
  <div class="sb"><span class="sb-t">9:41</span><span class="sb-r"></span></div>
  <div class="ai-hdr" style="padding-bottom:4px"><button class="ai-back" aria-label="Indietro" onclick="goBack()">‹</button></div>
  <div style="padding:0 24px 18px"><div class="eyebrow">Memoria</div><div class="scr-title" style="margin-top:6px">Aggiungi dato</div></div>
  <div class="body" style="padding:0 24px 24px">
    <div class="prof-sec-l" style="padding:0;margin:0 0 12px">Tipo di registrazione</div>
    <div style="display:grid;grid-template-columns:1fr 1fr;gap:12px;margin-bottom:22px">
      <div style="padding:18px;background:var(--orange-soft);border:1.5px solid var(--line-orange);border-radius:16px;text-align:center;cursor:pointer">
        <svg width="26" height="26" viewBox="0 0 24 24" fill="none" stroke="var(--orange)" stroke-width="1.6" style="margin-bottom:8px"><path d="M12 19l7-7 3 3-7 7-3-3z"/><path d="M18 13l-1.5-1.5"/><path d="M2 22l4-1 13-13-3-3L3 18l-1 4z"/></svg>
        <div style="font-size:14px;font-weight:700;color:var(--navy)">Scrivi</div><div style="font-size:12px;color:var(--muted)">Nota libera</div>
      </div>
      <div style="padding:18px;background:#fff;border:1.5px solid var(--line);border-radius:16px;text-align:center;cursor:pointer;box-shadow:var(--sh-card)">
        <svg width="26" height="26" viewBox="0 0 24 24" fill="none" stroke="var(--navy)" stroke-width="1.6" style="margin-bottom:8px"><rect x="9" y="3" width="6" height="11" rx="3"/><path d="M5 11a7 7 0 0014 0M12 18v3" stroke-linecap="round"/></svg>
        <div style="font-size:14px;font-weight:700;color:var(--navy)">Audio</div><div style="font-size:12px;color:var(--muted)">Registra voce</div>
      </div>
      <div style="padding:18px;background:#fff;border:1.5px solid var(--line);border-radius:16px;text-align:center;cursor:pointer;box-shadow:var(--sh-card)">
        <svg width="26" height="26" viewBox="0 0 24 24" fill="none" stroke="var(--navy)" stroke-width="1.6" style="margin-bottom:8px"><path d="M21 12.5l-8.5 8.5a5 5 0 01-7-7l9-9a3.5 3.5 0 015 5l-9 9a1.5 1.5 0 01-2-2l8.5-8.5" stroke-linecap="round" stroke-linejoin="round"/></svg>
        <div style="font-size:14px;font-weight:700;color:var(--navy)">Documento</div><div style="font-size:12px;color:var(--muted)">Carica file</div>
      </div>
      <div style="padding:18px;background:#fff;border:1.5px solid var(--line);border-radius:16px;text-align:center;cursor:pointer;box-shadow:var(--sh-card)">
        <svg width="26" height="26" viewBox="0 0 24 24" fill="none" stroke="var(--navy)" stroke-width="1.6" style="margin-bottom:8px"><rect x="3" y="5" width="18" height="15" rx="2"/><circle cx="9" cy="11" r="2"/><path d="M3 18l5-4 4 3 3-2 6 5" stroke-linecap="round" stroke-linejoin="round"/></svg>
        <div style="font-size:14px;font-weight:700;color:var(--navy)">Foto</div><div style="font-size:12px;color:var(--muted)">Scatta o carica</div>
      </div>
    </div>
    <div class="prof-sec-l" style="padding:0;margin:0 0 10px">Nota</div>
    <textarea class="input" style="height:110px;padding:14px 18px;resize:none" placeholder="Scrivi cosa vuoi ricordare di oggi…"></textarea>
  </div>
  <div class="pad" style="padding-bottom:30px"><button class="btn btn-primary" onclick="goBack()">Salva nell'archivio</button></div>
</div>

<!-- ═══ AI CHAT ═══ -->
<div class="screen" id="s-ai">
  <div class="sb"><span class="sb-t">9:41</span><span class="sb-r"></span></div>
  <div class="ai-hdr">
    <button class="ai-back" onclick="closeAi()">‹</button>
    <img src="logo dot.png" alt="DOT" style="height:32px;display:block">
    <div style="margin-left:auto;font-size:12px;color:var(--muted)">Assistente</div>
  </div>
  <div class="chat-msgs" id="chat-msgs">
    <div class="empty-note">Il tuo Phenotype è pronto.<br>Cosa vuoi sapere oggi?</div>
  </div>
  <div class="preset-row">
    <div class="pchip hi" onclick="sendPreset(this)">Mi alleno oggi?</div>
    <div class="pchip" onclick="sendPreset(this)">Come sto dormendo?</div>
    <div class="pchip" onclick="sendPreset(this)">Cosa mangio stasera?</div>
  </div>
  <div class="chat-inp-row">
    <input class="chat-inp" id="chat-in" placeholder="Scrivi a DOT…" onkeydown="if(event.key==='Enter')sendMsg()">
    <button class="send-btn" aria-label="Invia messaggio" onclick="sendMsg()"><svg width="18" height="18" viewBox="0 0 24 24" fill="#fff"><path d="M2 21l21-9L2 3v7l15 2-15 2z"/></svg></button>
  </div>
</div>

<!-- ═══ PROFILO ═══ -->
<div class="screen" id="s-profile">
  <div class="sb"><span class="sb-t">9:41</span><span class="sb-r"></span></div>
  <div class="hdr-row"><button class="ai-back" onclick="switchTab('home')">‹</button><div></div></div>
  <div class="body" style="padding-bottom:20px">
    <div class="prof-hero">
      <div class="prof-av">G</div>
      <div class="prof-name">Giulia Ferretti</div>
      <div class="prof-meta">Profilo attivo · 5 fonti connesse</div>
    </div>
    <!-- Completamento Phenotype: quanti input disponibili hai attivato -->
    <div class="prof-sec-l">Completamento del Phenotype</div>
    <div class="prof-card" style="padding:18px 20px">
      <div class="cmp-row">
        <div class="cmp-head"><span class="cmp-name">Fisico</span><span class="cmp-pct">80%</span></div>
        <div class="cmp-bar"><div class="cmp-fill" style="width:80%"></div></div>
        <div class="cmp-note">4 di 5 fonti attive · manca alimentazione</div>
      </div>
      <div class="cmp-row">
        <div class="cmp-head"><span class="cmp-name">Mentale</span><span class="cmp-pct">40%</span></div>
        <div class="cmp-bar"><div class="cmp-fill" style="width:40%"></div></div>
        <div class="cmp-note">2 di 5 fonti attive · aggiungi note e umore</div>
      </div>
      <div class="cmp-row">
        <div class="cmp-head"><span class="cmp-name">Abitudini</span><span class="cmp-pct">100%</span></div>
        <div class="cmp-bar"><div class="cmp-fill" style="width:100%"></div></div>
        <div class="cmp-note">Tutte le fonti attive</div>
      </div>
    </div>

    <!-- Esporta / scarica archivio -->
    <div class="prof-sec-l">Il tuo archivio</div>
    <div class="prof-card">
      <div class="prof-row" onclick="exportArchive(this)">
        <div class="pri-ico"><i class="ti ti-download"></i></div>
        <div><div class="pri-name">Esporta il tuo archivio</div><div class="pri-sub">Scarica tutti i tuoi dati cifrati</div></div>
        <i class="ti ti-chevron-right" style="margin-left:auto;color:var(--muted)"></i>
      </div>
    </div>

    <!-- Calendario mese compatto con pallini -->
    <div class="prof-sec-l">Calendario delle note</div>
    <div class="prof-card" style="padding:18px 18px 20px">
      <div class="cal-head"><button class="cal-nav" aria-label="Mese precedente"><i class="ti ti-chevron-left"></i></button>
        <span class="cal-title">Giugno 2026</span>
        <button class="cal-nav" aria-label="Mese successivo"><i class="ti ti-chevron-right"></i></button></div>
      <div class="cal-wd"><span>L</span><span>M</span><span>M</span><span>G</span><span>V</span><span>S</span><span>D</span></div>
      <div class="cal-grid" id="cal-grid"></div>
      <div class="cal-legend"><span class="cal-dot has"></span> con nota · <span class="cal-dot"></span> senza</div>
    </div>

    <div class="prof-sec-l">App collegate</div>
    <div class="prof-card">
      <div class="prof-row"><div class="pri-ico">♥</div><div><div class="pri-name">Apple Health</div><div class="pri-sub">Battiti · Passi · Sonno</div></div><div class="pri-badge on">Attiva</div></div>
      <div class="prof-row"><div class="pri-ico">⚡</div><div><div class="pri-name">Strava</div><div class="pri-sub">Corsa · Ciclismo</div></div><div class="pri-badge on">Attiva</div></div>
      <div class="prof-row" onclick="go('s-raccolta')"><div class="pri-ico">🥗</div><div><div class="pri-name">Yuka</div><div class="pri-sub">Qualità alimentare</div></div><div class="pri-badge off">Collega</div></div>
    </div>
    <div class="prof-sec-l">Wearable connesso</div>
    <div class="prof-card">
      <div class="prof-row"><div class="pri-ico">⌚</div><div><div class="pri-name">Apple Watch</div><div class="pri-sub">HRV · SpO₂ · Sonno</div></div><div class="pri-badge on">Connesso</div></div>
    </div>
    <div class="prof-sec-l">Impostazioni</div>
    <div class="prof-card">
      <div class="prof-row"><div class="pri-ico">🔒</div><div><div class="pri-name">Privacy e cifratura</div><div class="pri-sub">AES-256 · Dati sotto il tuo controllo</div></div></div>
      <div class="prof-row"><div class="pri-ico">🔔</div><div><div class="pri-name">Notifiche</div><div class="pri-sub">Osservazioni quotidiane</div></div></div>
    </div>
    <div class="pad" style="padding:8px 24px 0"><button class="btn btn-ghost" onclick="go('s-splash')">Esci</button></div>
  </div>
</div>

<!-- ═══ DOT OVERLAY ═══ -->
<div class="overlay" id="overlay" onclick="closeOverlayBg(event)">
  <div class="ovl-sheet">
    <div class="ovl-handle" onclick="closeOverlay()"></div>
    <div class="ovl-hdr">
      <div class="wave-mark" style="width:34px;height:34px"></div>
      <div class="ovl-title">Parla con DOT</div>
      <button class="ovl-close" onclick="closeOverlay()">✕</button>
    </div>
    <div class="preset-row">
      <div class="pchip hi" onclick="sendOverlayPreset(this)">Mi alleno oggi?</div>
      <div class="pchip" onclick="sendOverlayPreset(this)">Come sto dormendo?</div>
      <div class="pchip" onclick="sendOverlayPreset(this)">Cosa mangio stasera?</div>
    </div>
    <div class="ovl-chat" id="ovl-msgs">
      <div class="empty-note">Il tuo Phenotype è pronto.<br>Cosa vuoi sapere oggi?</div>
    </div>
    <div class="ovl-inp-row">
      <input class="chat-inp" id="ovl-in" placeholder="Scrivi a DOT…" onkeydown="if(event.key==='Enter')sendOvl()">
      <button class="send-btn" aria-label="Invia messaggio" onclick="sendOvl()"><svg width="18" height="18" viewBox="0 0 24 24" fill="#fff"><path d="M2 21l21-9L2 3v7l15 2-15 2z"/></svg></button>
    </div>
  </div>
</div>

</div><!-- /phone -->
<script>
/* ═══ NAVIGATION ═══ */
let hist=['s-splash'],cur='s-splash',aiReturn='s-home';
function go(id){
  if(id===cur||!document.getElementById(id))return;
  const prev=document.getElementById(cur),next=document.getElementById(id);
  prev.classList.add('exit-left');prev.classList.remove('active');
  next.style.transition='none';next.style.transform='translateX(100%)';next.classList.add('active');
  requestAnimationFrame(()=>{next.style.transition='';next.style.transform='';
    setTimeout(()=>{prev.classList.remove('exit-left');prev.style.transform='';},350);});
  hist.push(id);cur=id;
  if(window.__homeCloud){
    if(id==='s-home')setTimeout(window.__homeCloud.start,360);
    else window.__homeCloud.stop();
  }
}
function goBack(){
  if(hist.length<2)return;hist.pop();const prev=hist[hist.length-1];
  const from=document.getElementById(cur),to=document.getElementById(prev);if(!to)return;
  from.style.transition='transform .28s cubic-bezier(.4,0,.2,1)';from.style.transform='translateX(100%)';
  to.style.transition='none';to.style.transform='translateX(-15%)';to.classList.add('active');
  requestAnimationFrame(()=>{to.style.transition='transform .28s cubic-bezier(.4,0,.2,1)';to.style.transform='';
    setTimeout(()=>{from.classList.remove('active');from.style.transform='';from.style.transition='';to.style.transition='';},290);});
  cur=prev;
}
function flowNav(){
  document.querySelectorAll('.bnav').forEach(b=>{
    b.classList.remove('flowing');void b.offsetWidth;b.classList.add('flowing');
  });
}
function switchTab(tab){
  flowNav();
  const map={home:'s-home',vault:'s-vault',profile:'s-profile'};
  const id=map[tab];if(!id||id===cur)return;
  document.getElementById(cur).classList.remove('active');
  const next=document.getElementById(id);next.style.transition='none';next.style.transform='';next.classList.add('active');
  cur=id;hist=[id];
  if(id==='s-home'){dynamicPhrase();renderHome(document.querySelector('#home-chips .chip.on').dataset.f);
    if(window.__homeCloud)setTimeout(window.__homeCloud.start,60);}
  else if(window.__homeCloud){window.__homeCloud.stop();}
  if(id==='s-vault'){setTimeout(startNet,80);}else{stopNet();}
  if(id==='s-profile'){renderCalendar();}
}
function closeAi(){ // AI chat is opened from overlay; back returns to last tab
  document.getElementById('s-ai').classList.remove('active');
  const to=document.getElementById(aiReturn);to.style.transition='none';to.style.transform='';to.classList.add('active');
  cur=aiReturn;hist=[aiReturn];
}

/* ═══ OVERLAY ═══ */
function openOverlay(){flowNav();document.getElementById('overlay').classList.add('open');setTimeout(()=>document.getElementById('ovl-in').focus(),420)}
function closeOverlay(){document.getElementById('overlay').classList.remove('open')}
function closeOverlayBg(e){if(e.target===e.currentTarget)closeOverlay()}

/* ═══ DRUM PICKER ═══ */
function buildDrum(id,min,max,init){
  const d=document.getElementById(id);if(!d)return;
  d.innerHTML='<div class="drum-item" style="opacity:0">0</div><div class="drum-item" style="opacity:0">0</div>';
  for(let i=min;i<=max;i++){const el=document.createElement('div');el.className='drum-item';el.textContent=i;d.appendChild(el);}
  d.innerHTML+='<div class="drum-item" style="opacity:0">0</div><div class="drum-item" style="opacity:0">0</div>';
  d.scrollTop=(init-min+2)*72;updateDrum(d);
}
function updateDrum(d){
  const items=[...d.querySelectorAll('.drum-item')].filter(el=>el.style.opacity!=='0');
  const ci=Math.round(d.scrollTop/72);
  items.forEach((it,i)=>{it.classList.remove('selected','near');const diff=Math.abs(i-ci);if(diff===0)it.classList.add('selected');else if(diff===1)it.classList.add('near');});
}
function onDrum(d){clearTimeout(d._t);d._t=setTimeout(()=>{d.scrollTo({top:Math.round(d.scrollTop/72)*72,behavior:'smooth'});updateDrum(d);},80);updateDrum(d);}
buildDrum('drum-age',14,90,28);
buildDrum('drum-weight',35,200,75);
buildDrum('drum-height',120,220,165);

/* multi-select & single-select for profilazione */
function multiSel(el){el.classList.toggle('on');}
function singleSel(el){el.closest('.sel-list').querySelectorAll('.sel-item').forEach(x=>x.classList.remove('on'));el.classList.add('on');}

/* ═══ SOURCE TOGGLE / SELECTIONS ═══ */
function toggleSrc(row){const b=row.querySelector('.pri-badge');const on=b.classList.contains('on');
  b.classList.toggle('on',!on);b.classList.toggle('off',on);b.textContent=on?'Collega':'Connesso';}
function selDay(el){el.closest('.week').querySelectorAll('.wd').forEach(x=>x.classList.remove('on'));el.classList.add('on');}
function openDoc(name){openOverlay();setTimeout(()=>{const m=document.getElementById('ovl-msgs');m.innerHTML='';
  addMsg(m,'Leggimi il documento: '+name,'user');setTimeout(()=>addMsg(m,getReply(name.toLowerCase()),'ai'),800);},300);}

/* ═══ INSIGHT DATA — tono editoriale-archivio ═══ */
const INSIGHTS=[
  {f:'attivita',src:'Referto + Strava',srcIcon:'ti-file-text',ctx:'Oggi · 18:30 · Bologna',
   title:'Diagnostica allenamenti',
   peek:'Hai un nuovo referto nel fascicolo: ti mostro come leggerlo insieme ai tuoi ultimi dati di allenamento.',
   body:'L\'Ecocolordoppler nel fascicolo riporta valori nella norma. Letto insieme alle tue ultime uscite, nessun parametro limita il carico attuale: puoi proseguire al ritmo di questa settimana.',
   recoLabel:'Cosa puoi fare', reco:'Mantieni il volume attuale. <b>Riporta il referto al medico al prossimo controllo.</b>',
   rationale:'Referto del 10/05 · 4 uscite/settimana · HR medio 148 bpm — da Fascicolo + Strava',
   illus:'referto', prompt:'Collega il mio ultimo referto ai dati di allenamento recenti'},

  {f:'benessere',src:'Google Calendar',srcIcon:'ti-calendar',ctx:'Oggi · 08:00 · Bologna',
   title:'Giornata impegnativa?',
   peek:'Oggi il calendario è pieno e hai poco margine: meglio un allenamento breve o solo mobilità.',
   body:'Sei coperta di impegni dalle 9 alle 19, con due blocchi senza pause. In giornate così, una sessione lunga rischia di saltare o di pesare troppo.',
   recoLabel:'Cosa puoi fare', reco:'Punta su <b>20 minuti di mobilità</b> tra un blocco e l\'altro, invece di un allenamento pieno.',
   rationale:'7 eventi · 9:00–19:00 · 1 pausa libera alle 13:30 — da Google Calendar',
   illus:'calendar', prompt:'Come organizzo l\'allenamento in una giornata così piena?'},

  {f:'benessere',src:'Yuka',srcIcon:'ti-leaf',ctx:'Oggi · 13:10 · Bologna',
   title:'Hai già tutto, ti va una Poké?',
   peek:'Hai fatto un allenamento intenso ieri: ti consiglio qualcosa di semplice e proteico stasera.',
   body:'Dopo lo sforzo di ieri il corpo chiede recupero. Con gli ingredienti che hai scansionato con Yuka puoi mettere insieme un piatto unico, senza conteggi.',
   recoLabel:'Idea per stasera', reco:'Riso, salmone, avocado, edamame e salsa teriyaki. <b>Pronto in 15 minuti.</b>',
   rationale:'Allenamento intenso ieri 20:30 · 5 ingredienti idonei in dispensa — da Strava + Yuka',
   illus:'food', prompt:'Cosa posso cucinare di semplice con quello che ho scansionato?'},

  {f:'attivita',src:'Strava',srcIcon:'ti-bolt',ctx:'Oggi · 18:30 · Bologna',
   title:'Corsa di routine o sfogo serale?',
   peek:'Oggi hai allenato forte: chissà se era per sfogare la pressione o eri in mood super atleta.',
   body:'Hai chiuso 9,8 km in 59 minuti, sopra il tuo passo abituale. Un picco isolato va benissimo; se diventa abitudine serale, vale la pena ascoltarne il motivo.',
   recoLabel:'Cosa puoi fare', reco:'Domani <b>zona 2 leggera o riposo</b>, per consolidare lo sforzo di oggi.',
   rationale:'9,8 km · 59:46 · passo 6:05/km · +9% sul tuo medio — da Strava',
   illus:'gps', prompt:'Analizza la corsa di oggi rispetto alla mia media'},

  {f:'sonno',src:'Apple Watch',srcIcon:'ti-moon',ctx:'Stanotte · 07:10 · Bologna',
   title:'Terza notte di sonno profondo basso',
   peek:'Il sonno profondo è sotto la tua norma da tre notti: un pattern che vale la pena osservare.',
   body:'Hai dormito circa 7 ore, ma la quota di sonno profondo resta bassa da tre notti. Non è un allarme: è spesso ciò che spiega una stanchezza che si accumula senza causa evidente.',
   recoLabel:'Cosa puoi fare', reco:'Stasera <b>anticipa di 30 minuti</b> e riduci gli schermi dopo le 22.',
   rationale:'7h 04min · profondo 14% (norma 18–20%) · 3 notti — da Apple Watch',
   illus:'sleep', prompt:'Cosa dicono le mie ultime notti di sonno?'},
];

/* ═══ frase dinamica: fascia oraria + ultimo dato in input ═══ */
function dynamicPhrase(){
  const el=document.getElementById('obs-phrase');if(!el)return;
  const h=new Date().getHours();
  let saluto;
  if(h<6) saluto='\u00c8 notte fonda, Giulia.';
  else if(h<12) saluto='Buongiorno, Giulia.';
  else if(h<18) saluto='Buon pomeriggio, Giulia.';
  else saluto='Buonasera, Giulia.';
  const ultimi=[
    'Apple Watch ha appena <span class="hl">chiuso la tua notte</span>.',
    'Strava ha registrato <span class="hl">la corsa di oggi</span>.',
    '\u00c8 arrivato <span class="hl">un nuovo referto</span> nel fascicolo.',
    'Il calendario di oggi \u00e8 <span class="hl">fitto di impegni</span>.'
  ];
  const idx=h<10?0:(h<14?2:(h<20?1:3));
  el.innerHTML=saluto+' '+ultimi[idx];
}

/* ═══ illustrazioni figurative caratterizzanti (dot-matrix + figura della fonte) ═══ */
function illusSVG(type){
  const o='#D98324', n='#2B2118', cream='#FAF4EC';
  const W='<svg viewBox="0 0 330 190" width="100%" height="100%" preserveAspectRatio="xMidYMid slice" aria-hidden="true">';
  if(type==='referto'){ // documento medico stilizzato
    let g='<rect width="330" height="190" fill="'+cream+'"/>';
    g+='<rect x="95" y="28" width="140" height="150" rx="8" fill="#fff" stroke="'+n+'" stroke-opacity=".18"/>';
    g+='<rect x="110" y="42" width="70" height="9" rx="3" fill="'+n+'" opacity=".7"/>';
    g+='<rect x="110" y="58" width="110" height="5" rx="2" fill="'+n+'" opacity=".25"/>';
    for(let r=0;r<6;r++){g+='<rect x="110" y="'+(80+r*15)+'" width="'+(70-r*6)+'" height="5" rx="2" fill="'+n+'" opacity=".2"/>';
      g+='<rect x="'+(192)+'" y="'+(80+r*15)+'" width="28" height="5" rx="2" fill="'+(r===2?o:n)+'" opacity="'+(r===2?1:.2)+'"/>';}
    g+='<circle cx="215" cy="158" r="13" fill="'+o+'"/><path d="M209 158l4 4 8-8" stroke="#fff" stroke-width="2.4" fill="none" stroke-linecap="round" stroke-linejoin="round"/>';
    return W+g+'</svg>';
  }
  if(type==='calendar'){ // giornata a blocchi (screenshot calendar)
    let g='<rect width="330" height="190" fill="'+cream+'"/>';
    const blocks=[[36,60,'#378ADD'],[96,38,'#7F77DD'],[150,46,o],[210,30,'#1D9E75'],[248,40,'#D4537E']];
    g+='<line x1="70" y1="20" x2="70" y2="178" stroke="'+n+'" stroke-opacity=".12"/>';
    for(let t=0;t<5;t++)g+='<text x="56" y="'+(34+t*34)+'" font-size="9" fill="'+n+'" opacity=".4" text-anchor="end" font-family="-apple-system,sans-serif">'+(9+t*2)+':00</text>';
    blocks.forEach(b=>{g+='<rect x="80" y="'+b[0]+'" width="170" height="'+(b[1]-4)+'" rx="6" fill="'+b[2]+'" opacity="'+(b[2]===o?1:.85)+'"/>';});
    g+='<rect x="80" y="150" width="170" height="22" rx="6" fill="none" stroke="'+o+'" stroke-width="1.5" stroke-dasharray="4 4"/>';
    return W+g+'</svg>';
  }
  if(type==='food'){ // bowl / poke vista dall'alto
    let g='<rect width="330" height="190" fill="'+cream+'"/>';
    g+='<circle cx="165" cy="95" r="68" fill="#fff" stroke="'+n+'" stroke-opacity=".12"/>';
    g+='<circle cx="165" cy="95" r="56" fill="#FDEEE0"/>';
    const food=[[140,75,16,'#1D9E75'],[185,72,15,o],[150,110,15,'#D4537E'],[190,108,13,'#EF9F27'],[165,95,12,'#fff'],[128,98,11,'#9FE1CB'],[200,90,10,'#F0997B']];
    food.forEach(f=>{g+='<circle cx="'+f[0]+'" cy="'+f[1]+'" r="'+f[2]+'" fill="'+f[3]+'" stroke="'+n+'" stroke-opacity=".08"/>';});
    for(let i=0;i<8;i++){const a=i/8*6.28;g+='<circle cx="'+(165+Math.cos(a)*44)+'" cy="'+(95+Math.sin(a)*44)+'" r="3" fill="'+n+'" opacity=".25"/>';}
    return W+g+'</svg>';
  }
  if(type==='gps'){ // tracciato corsa + tempo
    let g='<rect width="330" height="190" fill="'+cream+'"/>';
    g+='<path d="M70 130 C90 90, 120 95, 130 70 S175 40, 200 60 S250 70, 245 100 S210 140, 175 130 S110 150, 95 140" fill="none" stroke="'+o+'" stroke-width="3.5" stroke-linecap="round" stroke-linejoin="round"/>';
    g+='<circle cx="70" cy="130" r="6" fill="'+o+'"/><circle cx="70" cy="130" r="11" fill="none" stroke="'+o+'" stroke-opacity=".35" stroke-width="2"/>';
    g+='<circle cx="95" cy="140" r="5" fill="'+n+'"/>';
    g+='<text x="248" y="40" font-size="11" font-weight="700" fill="'+n+'" text-anchor="end" font-family="-apple-system,sans-serif" opacity=".5">59:46</text>';
    return W+g+'</svg>';
  }
  // sleep: tre notti a barre di punti, terza bassa
  let g='<rect width="330" height="190" fill="'+cream+'"/>';
  const heights=[6,5,3]; const labels=['2 notti fa','ieri','stanotte'];
  for(let b=0;b<3;b++){
    for(let r=0;r<6;r++){const on=r<heights[b];const isLow=(b===2);
      g+='<circle cx="'+(95+b*70)+'" cy="'+(150-r*20)+'" r="6" fill="'+(on?(isLow?o:n):n)+'" opacity="'+(on?(isLow?1:.75):.12)+'"/>';}
    g+='<text x="'+(95+b*70)+'" y="172" font-size="9" fill="'+n+'" opacity=".45" text-anchor="middle" font-family="-apple-system,sans-serif">'+labels[b]+'</text>';
  }
  return W+g+'</svg>';
}

/* ═══ CARD ACCORDION accessibile ═══ */
let stackList=[],openIdx=-1;
function insCardHTML(ins,idx){
  const open=idx===openIdx;
  return '<div class="ins-card'+(open?' open':'')+'" data-f="'+ins.f+'">'+
    '<button class="ins-head" aria-expanded="'+open+'" aria-controls="full-'+idx+'" aria-label="'+ins.title+' — tocca per approfondire" onclick="toggleCard('+idx+')">'+
      '<span class="ins-expand" aria-hidden="true"><svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.2"><path d="M6 9l6 6 6-6" stroke-linecap="round" stroke-linejoin="round"/></svg></span>'+
      '<div class="ins-meta">'+
        '<span class="ins-source"><span class="si"><i class="ti '+ins.srcIcon+'" aria-hidden="true"></i></span>'+ins.src+'</span>'+
        '<span class="ins-ctx">'+ins.ctx+'</span>'+
      '</div>'+
      '<div class="ins-title">'+ins.title+'</div>'+
      '<div class="ins-peek">'+ins.peek+'</div>'+
    '</button>'+
    '<div class="ins-full" id="full-'+idx+'" role="region">'+
      '<div class="full-illus">'+illusSVG(ins.illus)+'</div>'+
      '<div class="full-body">'+ins.body+'</div>'+
      '<div class="full-reco"><span class="reco-l">'+ins.recoLabel+'</span><span class="reco-t">'+ins.reco+'</span></div>'+
      '<div class="full-rationale"><svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="#8A5114" stroke-width="2"><circle cx="12" cy="12" r="9"/><circle cx="12" cy="12" r="2.5" fill="#8A5114"/></svg><span>'+ins.rationale+'</span></div>'+
      '<div class="full-actions">'+
        '<button class="react-btn" aria-label="Utile" onclick="react(this)"><svg viewBox="0 0 24 24"><path d="M12 21s-7-4.5-9.5-9C.5 8 2.5 4 6 4c2 0 3 1.2 4 2.5C11 5.2 12 4 14 4c3.5 0 5.5 4 3.5 8-2.5 4.5-9.5 9-9.5 9z"/></svg></button>'+
        '<button class="react-btn" aria-label="Non utile" onclick="react(this)"><svg viewBox="0 0 24 24" style="transform:rotate(180deg)"><path d="M12 21s-7-4.5-9.5-9C.5 8 2.5 4 6 4c2 0 3 1.2 4 2.5C11 5.2 12 4 14 4c3.5 0 5.5 4 3.5 8-2.5 4.5-9.5 9-9.5 9z"/></svg></button>'+
        '<button class="full-cta" onclick="approfondisci('+idx+')">Chiedi a DOT</button>'+
      '</div>'+
    '</div>'+
  '</div>';
}
function toggleCard(i){
  openIdx=(openIdx===i)?-1:i;
  const wrap=document.getElementById('home-stack');
  [...wrap.children].forEach((c,idx)=>{
    const open=idx===openIdx;
    c.classList.toggle('open',open);
    const head=c.querySelector('.ins-head');head.setAttribute('aria-expanded',open);
  });
  if(openIdx>-1){const card=wrap.children[openIdx];setTimeout(()=>{const body=document.querySelector('#s-home .body');if(body){body.scrollTo({top:card.offsetTop-10,behavior:'smooth'});}},120);}
}
function renderHome(f){
  const wrap=document.getElementById('home-stack');if(!wrap)return;
  stackList=(f==='tutti')?INSIGHTS:INSIGHTS.filter(x=>x.f===f);
  openIdx=-1;
  wrap.innerHTML=stackList.map((ins,i)=>insCardHTML(ins,i)).join('');
}
function filterHome(el){el.closest('.chips-row').querySelectorAll('.chip').forEach(c=>c.classList.remove('on'));el.classList.add('on');renderHome(el.dataset.f);}
function filterVault(el){el.closest('.chips-row').querySelectorAll('.chip').forEach(c=>c.classList.remove('on'));el.classList.add('on');
  const f=el.dataset.f;document.querySelectorAll('#vault-data .data-row').forEach(r=>{r.style.display=(f==='tutti'||r.dataset.f===f)?'flex':'none';});}
function react(btn,dir){const sib=btn.parentElement.querySelectorAll('.react-btn');sib.forEach(b=>{if(b!==btn)b.classList.remove('on');});btn.classList.toggle('on');}
function approfondisci(idx){const ins=stackList[idx]||INSIGHTS[idx];aiReturn=cur;go('s-ai');
  setTimeout(()=>{const m=document.getElementById('chat-msgs');m.innerHTML='';
    addMsg(m,ins.prompt,'user');setTimeout(()=>addMsg(m,getReply(ins.prompt.toLowerCase()),'ai'),850);},460);}

/* ═══ CHAT ═══ */
const replies={
  'allena':'In base al tuo archivio: HRV stamattina 52ms, sotto la tua media del 12%. Oggi l\'osservazione suggerisce <strong>recupero attivo</strong> — 20 minuti in zona bassa, sotto 130bpm, sono più utili di una sessione intensa.',
  'dorm':'Ultime tre notti: 7h 04min in media, ma il <strong>sonno profondo è al 14%</strong>, sotto la tua norma del 18–20%. È il dato che spiega la stanchezza accumulata.',
  'mangi':'Oggi hai speso più del solito e l\'idratazione tracciata è bassa. Stasera l\'archivio legge un bisogno di <strong>qualcosa di caldo e semplice</strong> — niente conteggi, solo recupero.',
  'mal di testa':'Il mal di testa delle 14:45 arriva in una giornata con idratazione bassa e una notte di sonno profondo ridotto. <strong>Due segnali che spesso si sommano</strong>. Lo registro come pattern, non come allarme.',
  'referto':'Il referto più recente nel fascicolo riporta valori nella norma. Letto insieme ai tuoi allenamenti, <strong>nessun parametro limita il carico attuale</strong>. Te ne mostro la sintesi quando vuoi.',
  'analisi del sangue':'Analisi del sangue del 10:05: ferritina 68, vitamina D 42, emoglobina 15.2 — <strong>tutti nella norma</strong>. Nessun valore in conflitto con i tuoi dati di attività.',
  'visita medica':'Visita medica delle 12:17: archiviata e cifrata. Il referto è <strong>disponibile al Phenotype</strong> come contesto per le prossime osservazioni.',
  'recupero':'Recupero di oggi: HRV 52ms (−12%), sonno profondo ridotto da tre notti. L\'archivio legge <strong>un carico che si è accumulato</strong>. Una giornata più leggera riporterebbe i valori in linea.',
};
function getReply(q){const k=Object.keys(replies).find(k=>q.includes(k));return k?replies[k]:'Leggo il tuo Phenotype attuale — HRV 52ms, energia 64/100. <strong>L\'osservazione di oggi privilegia il recupero</strong>. Cosa vuoi approfondire?';}
function addMsg(c,txt,role){
  const w=document.createElement('div');const n=new Date();const ts=n.getHours()+':'+String(n.getMinutes()).padStart(2,'0');
  if(role==='user'){w.style.cssText='display:flex;flex-direction:column;align-items:flex-end';w.innerHTML='<div class="bubble-user">'+txt+'</div><div class="bubble-ts">'+ts+'</div>';}
  else{w.innerHTML='<div class="bubble-ai">'+txt+'</div><div class="bubble-ts">'+ts+'</div>';}
  c.appendChild(w);c.scrollTop=c.scrollHeight;
}
function sendPreset(el){const t=el.textContent;const m=document.getElementById('chat-msgs');if(m.querySelector('.empty-note'))m.innerHTML='';addMsg(m,t,'user');setTimeout(()=>addMsg(m,getReply(t.toLowerCase()),'ai'),800);}
function sendMsg(){const i=document.getElementById('chat-in');if(!i.value.trim())return;const t=i.value;i.value='';const m=document.getElementById('chat-msgs');if(m.querySelector('.empty-note'))m.innerHTML='';addMsg(m,t,'user');setTimeout(()=>addMsg(m,getReply(t.toLowerCase()),'ai'),900);}
function sendOverlayPreset(el){const t=el.textContent;const m=document.getElementById('ovl-msgs');if(m.querySelector('.empty-note'))m.innerHTML='';addMsg(m,t,'user');setTimeout(()=>addMsg(m,getReply(t.toLowerCase()),'ai'),800);}
function sendOvl(){const i=document.getElementById('ovl-in');if(!i.value.trim())return;const t=i.value;i.value='';const m=document.getElementById('ovl-msgs');if(m.querySelector('.empty-note'))m.innerHTML='';addMsg(m,t,'user');setTimeout(()=>addMsg(m,getReply(t.toLowerCase()),'ai'),900);}


/* ═══ RETE NODALE SFERICA — Memoria: Trigger(destra)→DOT→Insight(sinistra→Home) ═══ */
/* ═══ Memoria: interazioni rete ═══ */
function filterNet(el,kind){el.parentElement.querySelectorAll('.nf-chip').forEach(x=>x.classList.remove('on'));el.classList.add('on');
  const r=document.getElementById('net-reveal');if(r){r.classList.add('active');
    const t=el.textContent;r.innerHTML='Stai guardando i trigger di <b>'+t.toLowerCase()+'</b> · '+(t==='Oggi'?'4 segnali':(t==='Settimana'?'21 segnali':'80+ segnali'))+' nel flusso';}
}
function connectApp(card){const btn=card.querySelector('.ac-btn');if(btn.classList.contains('done'))return;
  btn.classList.add('done');btn.textContent='Collegata';}

function pingTrigger(el){el.classList.remove('ping');void el.offsetWidth;el.classList.add('ping');
  const r=document.getElementById('net-reveal');const app=el.dataset.app;
  const map={strava:'Strava invia <b>attività e performance</b> al tuo DOT',health:'Apple Health invia <b>battiti, passi e sonno</b>',watch:'Apple Watch invia <b>HRV e recupero</b>'};
  if(r&&map[app]){r.innerHTML=map[app];r.classList.add('active');}
}
function revealType(el,tipo){
  document.querySelectorAll('.net-type').forEach(x=>x.classList.remove('on'));el.classList.add('on');
  const r=document.getElementById('net-reveal');
  const map={'Attività':'Raccoglie <b>durata, intensità e frequenza</b> dei tuoi allenamenti','Sonno':'Raccoglie <b>fasi, durata e qualità</b> del riposo','Alimentazione':'Raccoglie <b>qualità e abitudini</b> alimentari','Referti':'Raccoglie <b>esami e documenti</b> dal fascicolo'};
  if(r){r.innerHTML='<b>'+tipo+'</b> · '+map[tipo];r.classList.add('active');}
}
let netRAF=null;
function drawNetStatic(){
  const cv=document.getElementById('net-canvas');if(!cv)return;const ctx=cv.getContext('2d');
  const dpr=Math.min(window.devicePixelRatio||1,2);cv.width=cv.clientWidth*dpr;cv.height=cv.clientHeight*dpr;
  const CX=cv.width/2,CY=cv.height/2,RR=Math.min(cv.width,cv.height)*0.27;
  ctx.fillStyle='#D98324';ctx.beginPath();ctx.arc(CX,CY,6*dpr,0,7);ctx.fill();
  for(let i=0;i<24;i++){const a=i/24*6.28;ctx.fillStyle='rgba(43,33,24,.4)';ctx.beginPath();ctx.arc(CX+Math.cos(a)*RR,CY+Math.sin(a)*RR,3*dpr,0,7);ctx.fill();}
}
function startNet(){
  if(window.matchMedia&&window.matchMedia("(prefers-reduced-motion:reduce)").matches){drawNetStatic();return;}
  const cv=document.getElementById('net-canvas');if(!cv)return;
  const ctx=cv.getContext('2d');
  const dpr=Math.min(window.devicePixelRatio||1,2);
  cv.width=cv.clientWidth*dpr;cv.height=cv.clientHeight*dpr;
  const W=()=>cv.width,H=()=>cv.height;
  const navy='#2B2118',orange='#D98324';
  const N=26,sphere=[];
  for(let i=0;i<N;i++){const phi=Math.acos(1-2*(i+0.5)/N);const theta=Math.PI*(1+Math.sqrt(5))*i;sphere.push({phi,theta});}
  const P=[];
  function spawn(){P.push({x:1.15,y:0.5+(Math.random()-0.5)*0.55,phase:'in',spd:0.004+Math.random()*0.004,dir:undefined});}
  for(let i=0;i<11;i++)spawn();
  let rot=0;
  function frame(){
    ctx.clearRect(0,0,W(),H());rot+=0.006;
    const CX=W()*0.5,CY=H()*0.5,RR=Math.min(W(),H())*0.27;
    const pts=sphere.map(s=>{const x=Math.sin(s.phi)*Math.cos(s.theta+rot);const y=Math.cos(s.phi);const z=Math.sin(s.phi)*Math.sin(s.theta+rot);return{sx:CX+x*RR,sy:CY+y*RR,z};});
    ctx.lineWidth=1*dpr;
    for(let i=0;i<pts.length;i++)for(let j=i+1;j<pts.length;j++){
      const dx=pts[i].sx-pts[j].sx,dy=pts[i].sy-pts[j].sy,d=Math.hypot(dx,dy);
      if(d<RR*0.85){const a=(1-d/(RR*0.85))*0.2*(((pts[i].z+pts[j].z)/2)+1)/2;ctx.strokeStyle='rgba(43,33,24,'+a+')';ctx.beginPath();ctx.moveTo(pts[i].sx,pts[i].sy);ctx.lineTo(pts[j].sx,pts[j].sy);ctx.stroke();}
    }
    pts.forEach(p=>{const f=(p.z+1)/2;ctx.fillStyle='rgba(43,33,24,'+(0.25+f*0.5)+')';ctx.beginPath();ctx.arc(p.sx,p.sy,(1.6+f*2)*dpr,0,7);ctx.fill();});
    const g=ctx.createRadialGradient(CX,CY,0,CX,CY,RR*0.55);g.addColorStop(0,'rgba(255,91,4,0.3)');g.addColorStop(1,'rgba(255,91,4,0)');
    ctx.fillStyle=g;ctx.beginPath();ctx.arc(CX,CY,RR*0.55,0,7);ctx.fill();
    ctx.fillStyle=orange;ctx.beginPath();ctx.arc(CX,CY,5*dpr,0,7);ctx.fill();
    for(let k=P.length-1;k>=0;k--){
      const p=P[k];let px,py;
      if(p.phase==='in'){p.x-=p.spd;px=p.x*W();py=(p.y+(0.5-p.y)*(1-(p.x-0.5)/0.65))*H();if(p.x<=0.52){p.phase='out';p.x=0.5;p.dir=(Math.random()-0.5)*2;}}
      else{p.x-=p.spd*1.1;const spread=(0.5-p.x)/0.5;px=p.x*W();py=(0.5+p.dir*spread*0.42)*H();}
      const r=(p.phase==='out'?2.4:1.8)*dpr;
      ctx.fillStyle=p.phase==='out'?orange:'rgba(43,33,24,0.55)';
      ctx.beginPath();ctx.arc(px,py,r,0,7);ctx.fill();
      ctx.strokeStyle=p.phase==='out'?'rgba(217,131,36,0.28)':'rgba(43,33,24,0.12)';
      ctx.lineWidth=r*0.8;ctx.beginPath();ctx.moveTo(px,py);ctx.lineTo(px+(p.phase==='out'?6:8)*dpr,py);ctx.stroke();
      if(p.x<-0.15){P.splice(k,1);spawn();}
    }
    if(P.length<11)spawn();
    netRAF=requestAnimationFrame(frame);
  }
  cancelAnimationFrame(netRAF);frame();
}
function stopNet(){if(netRAF)cancelAnimationFrame(netRAF);netRAF=null;}

dynamicPhrase();renderHome('tutti');

/* ═══ overview hook: ?screen=s-xxx mostra quella schermata all'avvio ═══ */
(function(){
  const p=new URLSearchParams(location.search);
  const s=p.get('screen');
  if(s){
    const el=document.getElementById(s);
    if(el){
      document.querySelectorAll('.screen').forEach(x=>{x.classList.remove('active');x.style.transition='none';x.style.transform='translateX(100%)';});
      el.classList.add('active');el.style.transform='translateX(0)';
      cur=s;hist=[s];
      // attiva animazioni dipendenti
      if(s==='s-home'){try{dynamicPhrase();renderHome('tutti');}catch(e){}}
      if(s==='s-vault'){try{setTimeout(startNet,120);}catch(e){}}
    }
  }
  if(p.get('chrome')==='off'){
    // nasconde il telaio del telefono per la griglia
    const ph=document.querySelector('.phone');
    if(ph){ph.style.boxShadow='none';ph.style.borderRadius='0';}
    const isl=document.querySelector('.island');if(isl)isl.style.display='none';
    document.documentElement.style.background='transparent';
    document.body.style.background='transparent';
  }
})();


/* a11y: rendi i div interattivi raggiungibili da tastiera */
(function(){
  function enhance(){
    document.querySelectorAll('[onclick]').forEach(el=>{
      if(el.tagName==='BUTTON'||el.tagName==='A')return;
      if(!el.hasAttribute('tabindex'))el.setAttribute('tabindex','0');
      if(!el.hasAttribute('role'))el.setAttribute('role','button');
      if(!el._kbd){el._kbd=true;el.addEventListener('keydown',e=>{
        if(e.key==='Enter'||e.key===' '){e.preventDefault();el.click();}
      });}
    });
  }
  enhance();
  // re-run after dynamic renders (home feed, etc.)
  const mo=new MutationObserver(()=>enhance());
  mo.observe(document.body,{childList:true,subtree:true});
})();

/* ═══ Profilo: calendario note ═══ */
function renderCalendar(){
  const g=document.getElementById('cal-grid');if(!g)return;
  const daysWithNote=new Set([2,5,6,9,11,12,16,18,19,23,26,11]); // giorni con nota (demo)
  const firstDow=0; // giugno 2026 inizia di lunedì (0=L)
  const total=30;
  let html='';
  for(let i=0;i<firstDow;i++)html+='<div class="cal-day empty"></div>';
  for(let d=1;d<=total;d++){
    const has=daysWithNote.has(d)?' has':'';
    const today=d===14?' today':'';
    html+='<div class="cal-day'+has+today+'" role="button" tabindex="0" aria-label="'+d+' giugno'+(has?', con nota':'')+'"><span>'+d+'</span><span class="cal-dot"></span></div>';
  }
  g.innerHTML=html;
}
function exportArchive(el){
  const n=el.querySelector('.pri-name');const orig=n.textContent;
  n.textContent='Preparazione export…';
  setTimeout(()=>{n.textContent='Archivio pronto · controlla i download';
    setTimeout(()=>{n.textContent=orig;},2200);},1100);
}

/* ═══ HOME BACKGROUND · node-cloud animato (sorgente: dot_node_cloud) ═══ */
(function(){
  const canvas=document.getElementById('home-node-cloud');
  if(!canvas)return;
  const stage=canvas.parentElement; // .home-bg
  const ctx=canvas.getContext('2d');
  const orange='#D98324';
  let raf=null,dpr=1,particles=[],rotation=0;
  const sphere=[],NODE_COUNT=26,PARTICLE_COUNT=11;
  for(let i=0;i<NODE_COUNT;i++){
    const phi=Math.acos(1-2*(i+0.5)/NODE_COUNT);
    const theta=Math.PI*(1+Math.sqrt(5))*i;
    sphere.push({phi,theta});
  }
  function resize(){
    dpr=Math.min(window.devicePixelRatio||1,2);
    const rect=stage.getBoundingClientRect();
    if(rect.width<2||rect.height<2)return;
    canvas.width=Math.round(canvas.clientWidth*dpr);
    canvas.height=Math.round(canvas.clientHeight*dpr);
  }
  function spawnParticle(){
    particles.push({x:1.15,y:0.5+(Math.random()-0.5)*0.55,phase:'in',
      speed:0.004+Math.random()*0.004,dir:0});
  }
  function frame(){
    const W=canvas.width,H=canvas.height;
    if(!W||!H){raf=requestAnimationFrame(frame);return;}
    const CX=W*0.5,CY=H*0.5,RR=Math.min(W,H)*0.34;
    ctx.clearRect(0,0,W,H);
    rotation+=0.006;
    const pts=sphere.map(function(s){
      const x=Math.sin(s.phi)*Math.cos(s.theta+rotation);
      const y=Math.cos(s.phi);
      const z=Math.sin(s.phi)*Math.sin(s.theta+rotation);
      return {sx:CX+x*RR,sy:CY+y*RR,z:z};
    });
    ctx.lineWidth=1*dpr;
    for(let i=0;i<pts.length;i++){
      for(let j=i+1;j<pts.length;j++){
        const dx=pts[i].sx-pts[j].sx,dy=pts[i].sy-pts[j].sy;
        const dist=Math.hypot(dx,dy);
        if(dist<RR*0.85){
          const depth=(((pts[i].z+pts[j].z)/2)+1)/2;
          const alpha=(1-dist/(RR*0.85))*0.2*depth;
          ctx.strokeStyle='rgba(43,33,24,'+alpha+')';
          ctx.beginPath();ctx.moveTo(pts[i].sx,pts[i].sy);ctx.lineTo(pts[j].sx,pts[j].sy);ctx.stroke();
        }
      }
    }
    pts.forEach(function(p){
      const f=(p.z+1)/2;
      ctx.fillStyle='rgba(43,33,24,'+(0.25+f*0.5)+')';
      ctx.beginPath();ctx.arc(p.sx,p.sy,(1.6+f*2)*dpr,0,Math.PI*2);ctx.fill();
    });
    const glow=ctx.createRadialGradient(CX,CY,0,CX,CY,RR*0.8);
    glow.addColorStop(0,'rgba(217,131,36,0.42)');
    glow.addColorStop(1,'rgba(217,131,36,0)');
    ctx.fillStyle=glow;ctx.beginPath();ctx.arc(CX,CY,RR*0.8,0,Math.PI*2);ctx.fill();
    ctx.fillStyle=orange;ctx.beginPath();ctx.arc(CX,CY,6*dpr,0,Math.PI*2);ctx.fill();
    for(let k=particles.length-1;k>=0;k--){
      const p=particles[k];let px,py;
      if(p.phase==='in'){
        p.x-=p.speed;px=p.x*W;
        py=(p.y+(0.5-p.y)*(1-(p.x-0.5)/0.65))*H;
        if(p.x<=0.52){p.phase='out';p.x=0.5;p.dir=(Math.random()-0.5)*2;}
      }else{
        p.x-=p.speed*1.1;const spread=(0.5-p.x)/0.5;px=p.x*W;
        py=(0.5+p.dir*spread*0.42)*H;
      }
      const r=(p.phase==='out'?2.4:1.8)*dpr;
      ctx.fillStyle=p.phase==='out'?orange:'rgba(43,33,24,0.55)';
      ctx.beginPath();ctx.arc(px,py,r,0,Math.PI*2);ctx.fill();
      ctx.strokeStyle=p.phase==='out'?'rgba(217,131,36,0.28)':'rgba(43,33,24,0.12)';
      ctx.lineWidth=r*0.8;ctx.beginPath();ctx.moveTo(px,py);
      ctx.lineTo(px+(p.phase==='out'?6:8)*dpr,py);ctx.stroke();
      if(p.x<-0.15){particles.splice(k,1);spawnParticle();}
    }
    while(particles.length<PARTICLE_COUNT)spawnParticle();
    raf=requestAnimationFrame(frame);
  }
  function startHomeCloud(){
    if(window.matchMedia&&window.matchMedia('(prefers-reduced-motion: reduce)').matches){return;}
    resize();
    if(!particles.length){for(let i=0;i<PARTICLE_COUNT;i++)spawnParticle();}
    cancelAnimationFrame(raf);frame();
  }
  function stopHomeCloud(){cancelAnimationFrame(raf);raf=null;}
  window.__homeCloud={start:startHomeCloud,stop:stopHomeCloud,resize:resize};
  window.addEventListener('resize',function(){resize();});
  // avvio iniziale se la home è già attiva
  setTimeout(function(){
    const home=document.getElementById('s-home');
    if(home&&home.classList.contains('active'))startHomeCloud();
  },200);
})();
</script>
</body>
</html>

