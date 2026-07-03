# Calculadora-TBH-DROP
Calcular quantos bau azul voce pode pegar por hora no TBH
<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>TBH • Calculadora de Drop — Baú Azul | RestBar Hero</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Chakra+Petch:wght@500;600;700&family=Rajdhani:wght@500;600;700&display=swap" rel="stylesheet">
<style>
  :root{
    --bg:#070b16;
    --bg2:#0b1224;
    --surface:#101a31;
    --surface2:#16223e;
    --line:#23335c;
    --rare:#2f8bff;
    --rare-soft:#5aa6ff;
    --fire1:#ff7a1a;
    --fire2:#ffc02e;
    --ember:#e6354a;
    --text:#eaf1ff;
    --muted:#8595bd;
    --muted2:#5e6e96;
    --shadow:0 24px 60px -20px rgba(0,0,0,.75);
  }
  *{box-sizing:border-box}
  html{-webkit-text-size-adjust:100%}
  body{
    margin:0;
    min-height:100vh;
    font-family:'Rajdhani',system-ui,sans-serif;
    color:var(--text);
    background:
      radial-gradient(1100px 600px at 78% -10%, rgba(47,139,255,.16), transparent 60%),
      radial-gradient(900px 500px at 0% 110%, rgba(255,122,26,.10), transparent 55%),
      linear-gradient(180deg,var(--bg) 0%, var(--bg2) 100%);
    background-attachment:fixed;
    padding:clamp(14px,3vw,40px);
  }
  .wrap{max-width:1060px;margin:0 auto}

  /* ---------- TOP BAR ---------- */
  .topbar{
    display:flex;align-items:center;gap:16px;flex-wrap:wrap;
    padding:14px 18px;
    border:1px solid var(--line);
    border-radius:18px;
    background:linear-gradient(180deg, rgba(22,34,62,.9), rgba(16,26,49,.9));
    box-shadow:var(--shadow);
  }
  .emblem{
    width:54px;height:54px;border-radius:13px;flex:0 0 auto;
    display:grid;place-items:center;
    background:radial-gradient(circle at 50% 30%, #1d2c52, #0a1126);
    border:1px solid #2c456f;
    box-shadow:0 0 0 1px rgba(255,255,255,.04) inset, 0 10px 24px -8px rgba(47,139,255,.5);
    position:relative;overflow:hidden;
  }
  .emblem svg{width:36px;height:36px}
  .brand{display:flex;flex-direction:column;line-height:1;gap:5px}
  .brand .game{
    font-family:'Chakra Petch';font-weight:700;letter-spacing:.14em;
    font-size:12px;color:var(--rare-soft);text-transform:uppercase;
  }
  .brand .name{
    font-family:'Chakra Petch';font-weight:700;font-size:clamp(20px,3.6vw,27px);
    letter-spacing:.02em;
    background:linear-gradient(92deg,#fff 0%, var(--fire2) 55%, var(--fire1) 100%);
    -webkit-background-clip:text;background-clip:text;color:transparent;
  }
  .topbar .spacer{flex:1 1 auto;min-width:8px}
  .handle{
    font-family:'Chakra Petch';font-weight:600;font-size:14px;color:var(--muted);
    padding:8px 13px;border:1px solid var(--line);border-radius:999px;
    background:rgba(10,17,38,.6);
  }
  .handle b{color:var(--text)}
  .live{
    display:inline-flex;align-items:center;gap:8px;
    font-family:'Chakra Petch';font-weight:700;font-size:12px;letter-spacing:.12em;
    padding:8px 13px;border-radius:999px;text-transform:uppercase;
    color:#ffd9dd;border:1px solid rgba(230,53,74,.5);
    background:linear-gradient(180deg, rgba(230,53,74,.28), rgba(230,53,74,.12));
  }
  .live .dot{width:9px;height:9px;border-radius:50%;background:#ff4d63;
    box-shadow:0 0 10px 2px #ff4d63;animation:blink 1.3s steps(2,jump-none) infinite}
  @keyframes blink{50%{opacity:.25}}

  /* ---------- HERO COPY ---------- */
  .lead{margin:26px 2px 18px}
  .eyebrow{
    font-family:'Chakra Petch';font-weight:700;letter-spacing:.22em;font-size:12px;
    color:var(--fire2);text-transform:uppercase;
  }
  .lead h1{
    margin:8px 0 6px;font-family:'Chakra Petch';font-weight:700;
    font-size:clamp(26px,5.4vw,44px);line-height:1.02;letter-spacing:.01em;
  }
  .lead h1 .blue{color:var(--rare-soft)}
  .lead p{margin:0;max-width:62ch;color:var(--muted);font-size:clamp(15px,2vw,17px);font-weight:500}

  /* ---------- CONTROL PANEL ---------- */
  .panel{
    margin-top:6px;border:1px solid var(--line);border-radius:20px;
    background:
      linear-gradient(180deg, rgba(22,34,62,.92), rgba(13,20,39,.92));
    box-shadow:var(--shadow);
    padding:clamp(18px,3vw,26px);position:relative;overflow:hidden;
  }
  .panel::before{
    content:"";position:absolute;inset:0;pointer-events:none;
    background:linear-gradient(90deg, rgba(255,122,26,.06), transparent 40%);
  }
  .panel-head{display:flex;align-items:baseline;justify-content:space-between;gap:12px;flex-wrap:wrap}
  .panel-head .label{
    font-family:'Chakra Petch';font-weight:700;letter-spacing:.04em;font-size:clamp(15px,2.4vw,18px);
  }
  .panel-head .hint{color:var(--muted2);font-size:13px;font-weight:600}
  .bonus-readout{
    display:flex;align-items:flex-end;gap:6px;margin:14px 0 4px;
  }
  #bonusBig{
    font-family:'Chakra Petch';font-weight:700;line-height:.9;
    font-size:clamp(52px,12vw,84px);
    background:linear-gradient(180deg,#fff, var(--fire2) 70%, var(--fire1));
    -webkit-background-clip:text;background-clip:text;color:transparent;
    font-variant-numeric:tabular-nums;
  }
  .bonus-readout .pct{font-family:'Chakra Petch';font-weight:700;font-size:clamp(24px,5vw,34px);color:var(--fire1);padding-bottom:8px}

  .slider-row{display:flex;align-items:center;gap:14px;margin-top:8px}
  input[type=range]{
    -webkit-appearance:none;appearance:none;width:100%;height:14px;border-radius:999px;
    background:
      linear-gradient(90deg, var(--fire1), var(--fire2)) 0/var(--fill,25%) 100% no-repeat,
      #0a1226;
    border:1px solid var(--line);cursor:pointer;outline:none;
  }
  input[type=range]::-webkit-slider-thumb{
    -webkit-appearance:none;width:28px;height:28px;border-radius:50%;
    background:radial-gradient(circle at 35% 30%, #fff3, transparent 60%), linear-gradient(180deg,#ffd76a,var(--fire1));
    border:2px solid #fff;box-shadow:0 0 0 4px rgba(255,122,26,.25), 0 6px 14px rgba(0,0,0,.5);cursor:grab;
  }
  input[type=range]::-moz-range-thumb{
    width:26px;height:26px;border-radius:50%;border:2px solid #fff;
    background:linear-gradient(180deg,#ffd76a,var(--fire1));box-shadow:0 0 0 4px rgba(255,122,26,.25);cursor:grab;
  }
  input[type=range]:focus-visible{box-shadow:0 0 0 3px rgba(90,166,255,.55)}

  .num-wrap{display:flex;align-items:center;border:1px solid var(--line);border-radius:12px;background:#0a1226;overflow:hidden;flex:0 0 auto}
  #bonusInput{
    width:104px;border:none;background:transparent;color:var(--text);
    font-family:'Chakra Petch';font-weight:700;font-size:20px;text-align:right;
    padding:10px 6px 10px 12px;outline:none;font-variant-numeric:tabular-nums;
    -moz-appearance:textfield;
  }
  #bonusInput::-webkit-outer-spin-button,#bonusInput::-webkit-inner-spin-button{-webkit-appearance:none;margin:0}
  .num-wrap .sign{padding:0 12px 0 4px;color:var(--fire1);font-family:'Chakra Petch';font-weight:700;font-size:18px}
  .num-wrap:focus-within{border-color:var(--fire1);box-shadow:0 0 0 3px rgba(255,122,26,.18)}

  .presets{display:flex;flex-wrap:wrap;gap:8px;margin-top:18px}
  .presets .lbl{align-self:center;color:var(--muted2);font-weight:600;font-size:13px;margin-right:2px}
  .chip{
    font-family:'Chakra Petch';font-weight:600;font-size:13px;letter-spacing:.02em;
    padding:8px 14px;border-radius:999px;cursor:pointer;
    color:var(--rare-soft);border:1px solid var(--line);background:rgba(47,139,255,.06);
    transition:transform .08s ease, background .15s, border-color .15s, color .15s;
  }
  .chip:hover{background:rgba(47,139,255,.16);border-color:var(--rare)}
  .chip:active{transform:translateY(1px)}
  .chip.active{color:#06101f;background:linear-gradient(180deg,var(--fire2),var(--fire1));border-color:transparent}

  /* ---------- LOOT CARDS ---------- */
  .grid{display:grid;grid-template-columns:1fr 1fr;gap:18px;margin-top:18px}
  .loot{
    --glow:.25;
    position:relative;border-radius:20px;overflow:hidden;
    border:1px solid rgba(47,139,255,.45);
    background:
      repeating-linear-gradient(135deg, rgba(47,139,255,.05) 0 12px, transparent 12px 24px),
      linear-gradient(180deg, #16264a, #0c1530);
    box-shadow:var(--shadow), 0 0 calc(34px*var(--glow)) rgba(47,139,255,calc(.7*var(--glow)));
    transition:box-shadow .35s ease, border-color .35s;
    padding:20px;
  }
  .loot::after{ /* rarity top sheen */
    content:"";position:absolute;left:0;right:0;top:0;height:3px;
    background:linear-gradient(90deg,transparent, var(--rare), transparent);
    opacity:calc(.4 + .6*var(--glow));
  }
  .loot-head{display:flex;align-items:center;justify-content:space-between;gap:10px}
  .rare-tag{
    font-family:'Chakra Petch';font-weight:700;letter-spacing:.16em;font-size:11px;
    color:#bfe0ff;text-transform:uppercase;
  }
  .item-id{font-family:'Chakra Petch';font-weight:600;font-size:12px;color:var(--muted2)}
  .chest-row{display:flex;align-items:center;gap:16px;margin:14px 0 4px}
  .chest{
    width:78px;height:78px;flex:0 0 auto;border-radius:14px;display:grid;place-items:center;
    background:radial-gradient(circle at 50% 30%, #16335f, #081026);
    border:1px solid #2c5896;
    box-shadow:0 0 calc(26px*var(--glow)) rgba(47,139,255,calc(.85*var(--glow))) , inset 0 0 18px rgba(0,0,0,.55);
    transition:box-shadow .35s ease;
  }
  .chest svg{width:50px;height:50px;display:block}
  .chest-row .title{font-family:'Chakra Petch';font-weight:700;font-size:clamp(16px,2.4vw,19px);line-height:1.1}
  .chest-row .sub{color:var(--muted);font-size:14px;font-weight:600;margin-top:3px}

  .stat-line{display:flex;justify-content:space-between;align-items:baseline;margin-top:14px;
    padding-top:14px;border-top:1px dashed var(--line)}
  .stat-line .k{color:var(--muted);font-weight:600;font-size:14px}
  .stat-line .v{font-family:'Chakra Petch';font-weight:700;color:#cfe0ff;font-variant-numeric:tabular-nums}

  .final{margin-top:14px}
  .final .k{display:flex;align-items:center;gap:8px;color:var(--muted);font-weight:600;font-size:13px;letter-spacing:.04em;text-transform:uppercase}
  .final .big{
    display:flex;align-items:baseline;gap:6px;margin-top:2px;
  }
  .final .big .num{
    font-family:'Chakra Petch';font-weight:700;line-height:.95;font-variant-numeric:tabular-nums;
    font-size:clamp(38px,8.5vw,56px);
    background:linear-gradient(180deg,#ffffff, var(--rare-soft) 75%, var(--rare));
    -webkit-background-clip:text;background-clip:text;color:transparent;
  }
  .final .big .u{font-family:'Chakra Petch';font-weight:700;font-size:clamp(20px,4vw,26px);color:var(--rare)}

  .bar{margin-top:12px;height:13px;border-radius:999px;background:#0a1226;border:1px solid var(--line);overflow:hidden;position:relative}
  .bar > span{display:block;height:100%;width:0%;border-radius:999px;
    background:linear-gradient(90deg, var(--rare), var(--rare-soft));
    box-shadow:0 0 16px rgba(47,139,255,.6);transition:width .45s cubic-bezier(.22,.9,.3,1)}
  .cap-note{margin-top:8px;font-size:12.5px;font-weight:600;color:var(--fire2);min-height:16px}

  /* ---------- FOOTER ---------- */
  .foot{
    margin-top:22px;display:flex;flex-wrap:wrap;gap:14px;align-items:center;justify-content:space-between;
    padding:16px 18px;border:1px solid var(--line);border-radius:16px;
    background:rgba(13,20,39,.7);
  }
  .formula{font-family:'Chakra Petch';font-weight:600;font-size:13.5px;color:var(--muted)}
  .formula code{color:var(--rare-soft);background:rgba(47,139,255,.1);padding:3px 8px;border-radius:7px}
  .media{display:flex;flex-wrap:wrap;gap:10px;align-items:center}
  .medbtn{
    display:inline-flex;align-items:center;gap:8px;text-decoration:none;
    font-family:'Chakra Petch';font-weight:700;font-size:13.5px;letter-spacing:.01em;
    padding:9px 15px;border-radius:999px;border:1px solid var(--line);
    color:var(--text);background:rgba(10,17,38,.6);
    transition:transform .08s ease, box-shadow .2s, border-color .2s, background .2s;
  }
  .medbtn svg{width:19px;height:19px;flex:0 0 auto}
  .medbtn:active{transform:translateY(1px)}
  .medbtn.yt{color:#ff5a5f}
  .medbtn.yt:hover{border-color:#ff5a5f;background:rgba(255,90,95,.12);box-shadow:0 0 18px rgba(255,90,95,.25)}
  .medbtn.yt span{color:var(--text)}
  .medbtn.dc{color:#7c8cff}
  .medbtn.dc:hover{border-color:#7c8cff;background:rgba(124,140,255,.12);box-shadow:0 0 18px rgba(124,140,255,.25)}
  .medbtn.dc span{color:var(--text)}
  .medbtn:focus-visible{outline:none;box-shadow:0 0 0 3px rgba(90,166,255,.5)}

  /* ---------- TIME PANEL READOUT ---------- */
  .panel + .panel{margin-top:18px}
  #timeBig{
    font-family:'Chakra Petch';font-weight:700;line-height:.9;
    font-size:clamp(52px,12vw,84px);
    background:linear-gradient(180deg,#fff, var(--rare-soft) 70%, var(--rare));
    -webkit-background-clip:text;background-clip:text;color:transparent;
    font-variant-numeric:tabular-nums;
  }
  .bonus-readout .min{font-family:'Chakra Petch';font-weight:700;font-size:clamp(20px,4.4vw,28px);color:var(--rare);padding-bottom:10px}
  input[type=range].blue{
    background:
      linear-gradient(90deg, var(--rare), var(--rare-soft)) 0/var(--fill,25%) 100% no-repeat,
      #0a1226;
  }
  input[type=range].blue::-webkit-slider-thumb{background:radial-gradient(circle at 35% 30%, #fff5, transparent 60%), linear-gradient(180deg,#bfe0ff,var(--rare));box-shadow:0 0 0 4px rgba(47,139,255,.25), 0 6px 14px rgba(0,0,0,.5)}
  input[type=range].blue::-moz-range-thumb{background:linear-gradient(180deg,#bfe0ff,var(--rare));box-shadow:0 0 0 4px rgba(47,139,255,.25)}
  .chip.blue{color:var(--rare-soft)}
  .chip.blue.active{color:#06101f;background:linear-gradient(180deg,#bfe0ff,var(--rare));border-color:transparent}
  #timeInput{width:96px}

  /* ---------- VERDICT CARD ---------- */
  .verdict{
    --vc:#3a8a3f;
    margin-top:18px;border-radius:20px;overflow:hidden;position:relative;
    border:1px solid color-mix(in srgb, var(--vc) 60%, var(--line));
    background:
      linear-gradient(180deg, color-mix(in srgb, var(--vc) 16%, #0d1426), color-mix(in srgb, var(--vc) 7%, #0b1120));
    box-shadow:var(--shadow), 0 0 36px color-mix(in srgb, var(--vc) 35%, transparent);
    transition:border-color .35s, box-shadow .35s, background .35s;
  }
  .verdict-top{display:flex;align-items:center;gap:14px;padding:18px 22px;border-bottom:1px solid rgba(255,255,255,.06);flex-wrap:wrap}
  .vc-swatch{width:46px;height:46px;border-radius:12px;flex:0 0 auto;background:var(--vc);
    box-shadow:0 0 22px color-mix(in srgb,var(--vc) 70%,transparent), inset 0 0 12px rgba(0,0,0,.4)}
  .vc-text{display:flex;flex-direction:column;gap:3px;min-width:0}
  .vc-rank{font-family:'Chakra Petch';font-weight:700;font-size:clamp(18px,3.4vw,24px);letter-spacing:.02em;color:#fff;text-transform:uppercase}
  .vc-note{color:var(--muted);font-size:14px;font-weight:600}
  .vc-cycle{margin-left:auto;text-align:right;flex:0 0 auto}
  .vc-cycle .lab{font-size:11px;letter-spacing:.12em;text-transform:uppercase;color:var(--muted2);font-weight:700;font-family:'Chakra Petch'}
  .vc-cycle .val{font-family:'Chakra Petch';font-weight:700;font-size:clamp(26px,5.6vw,38px);color:#fff;font-variant-numeric:tabular-nums;line-height:1}

  .vc-stats{display:grid;grid-template-columns:repeat(3,1fr);gap:1px;background:rgba(255,255,255,.06)}
  .vc-stat{background:#0c1426;padding:16px 18px;text-align:center}
  .vc-stat .k{font-size:11px;letter-spacing:.1em;text-transform:uppercase;color:var(--muted2);font-weight:700;font-family:'Chakra Petch'}
  .vc-stat .k small{letter-spacing:.04em;color:var(--rare-soft);text-transform:none}
  .vc-stat .v{font-family:'Chakra Petch';font-weight:700;font-size:clamp(22px,4.6vw,30px);margin-top:5px;color:#eaf1ff;font-variant-numeric:tabular-nums}
  .vc-stat .v small{font-size:14px;color:var(--muted);font-weight:600}

  /* efficiency bar */
  .eff-wrap{padding:16px 22px 20px;background:#0c1426}
  .eff-head{display:flex;justify-content:space-between;font-size:12.5px;font-weight:600;color:var(--muted);margin-bottom:8px}
  .eff-head b{color:#fff;font-family:'Chakra Petch'}
  .eff-bar{height:13px;border-radius:999px;background:#0a1226;border:1px solid var(--line);overflow:hidden}
  .eff-bar > span{display:block;height:100%;width:0%;border-radius:999px;background:linear-gradient(90deg,var(--vc),color-mix(in srgb,var(--vc) 50%, #fff));transition:width .45s cubic-bezier(.22,.9,.3,1), background .35s}

  /* ---------- PER-HOUR ON LOOT CARDS ---------- */
  .cards-intro{margin:18px 2px 0;color:var(--muted);font-size:14.5px;font-weight:600;line-height:1.5}
  .cards-intro b{color:var(--text)}
  .cards-intro .blue-t{color:var(--rare-soft)}
  .perhour{margin-top:12px;display:flex;align-items:center;justify-content:space-between;gap:10px;
    padding:12px 14px;border-radius:12px;background:rgba(47,139,255,.08);border:1px solid rgba(47,139,255,.25)}
  .perhour .k{font-size:12.5px;font-weight:700;color:var(--rare-soft);text-transform:uppercase;letter-spacing:.04em;font-family:'Chakra Petch'}
  .perhour .v{font-family:'Chakra Petch';font-weight:700;font-variant-numeric:tabular-nums;font-size:clamp(22px,4.5vw,28px);
    background:linear-gradient(180deg,#fff,var(--rare-soft));-webkit-background-clip:text;background-clip:text;color:transparent}
  .perhour .v small{font-size:12px;color:var(--muted);-webkit-text-fill-color:var(--muted);font-weight:600}

  /* ---------- RECOMMENDATIONS ---------- */
  .reco{margin-top:18px;border:1px solid var(--line);border-radius:20px;background:rgba(13,20,39,.7);padding:clamp(16px,3vw,24px);box-shadow:var(--shadow)}
  .reco h2{margin:0 0 4px;font-family:'Chakra Petch';font-weight:700;font-size:clamp(17px,3vw,20px)}
  .reco h2 .em{color:#5fd06a}
  .reco .desc{color:var(--muted);font-size:14px;font-weight:600;margin:0 0 16px}
  .reco-grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(120px,1fr));gap:10px}
  .reco-card{border:1px solid var(--line);border-radius:14px;padding:14px;text-align:center;background:#0c1426;position:relative;transition:border-color .2s, box-shadow .2s, transform .08s}
  .reco-card .n{font-size:11px;font-weight:700;letter-spacing:.06em;text-transform:uppercase;color:var(--muted2);font-family:'Chakra Petch'}
  .reco-card .t{font-family:'Chakra Petch';font-weight:700;font-size:clamp(24px,5vw,32px);margin:4px 0 6px;
    background:linear-gradient(180deg,#fff,#5fd06a);-webkit-background-clip:text;background-clip:text;color:transparent;font-variant-numeric:tabular-nums}
  .reco-card .azuis{display:flex;flex-direction:column;gap:4px}
  .az{display:flex;align-items:center;justify-content:center;gap:6px;font-size:12.5px;font-weight:600;color:var(--muted)}
  .az i{width:10px;height:10px;border-radius:3px;background:linear-gradient(180deg,#6fa8ef,#2f63b4);flex:0 0 auto;box-shadow:0 0 6px rgba(47,139,255,.5)}
  .az b{font-family:'Chakra Petch';color:var(--rare-soft);font-variant-numeric:tabular-nums;font-size:14px}
  .reco-summary{margin:16px 0 0;padding:14px 16px;border-radius:12px;background:rgba(95,208,106,.08);border:1px solid rgba(95,208,106,.28);
    color:var(--text);font-size:14.5px;font-weight:600;line-height:1.5}
  .reco-summary b{color:#7be087;font-family:'Chakra Petch'}
  .reco-card.hit{border-color:#5fd06a;box-shadow:0 0 22px rgba(95,208,106,.3)}
  .reco-card.hit::after{content:"VOCÊ ESTÁ AQUI";position:absolute;top:-9px;left:50%;transform:translateX(-50%);
    font-family:'Chakra Petch';font-weight:700;font-size:9px;letter-spacing:.08em;color:#06101f;background:#5fd06a;padding:3px 8px;border-radius:999px;white-space:nowrap}

  /* color legend */
  .legend{display:flex;flex-wrap:wrap;gap:8px 16px;margin-top:16px;padding-top:14px;border-top:1px solid var(--line)}
  .legend .it{display:flex;align-items:center;gap:7px;font-size:12.5px;font-weight:600;color:var(--muted)}
  .legend .sw{width:16px;height:16px;border-radius:4px;flex:0 0 auto}

  @media (max-width:720px){
    .vc-cycle{margin-left:0;text-align:left;width:100%}
    .vc-stat .v{font-size:22px}
  }
  @media (max-width:720px){
    .grid{grid-template-columns:1fr}
    .slider-row{flex-direction:column;align-items:stretch}
    .num-wrap{align-self:flex-end}
  }
  @media (prefers-reduced-motion:reduce){
    *{transition:none!important;animation:none!important}
  }
</style>
</head>
<body>
<div class="wrap">

  <!-- TOP BAR -->
  <header class="topbar">
    <div class="emblem">
      <!-- flaming sword emblem -->
      <svg viewBox="0 0 48 48" fill="none" xmlns="http://www.w3.org/2000/svg" aria-hidden="true">
        <defs>
          <linearGradient id="bl" x1="0" y1="0" x2="0" y2="1">
            <stop offset="0" stop-color="#bfe0ff"/><stop offset="1" stop-color="#2f8bff"/>
          </linearGradient>
          <linearGradient id="fl" x1="0" y1="0" x2="0" y2="1">
            <stop offset="0" stop-color="#ffd76a"/><stop offset="1" stop-color="#ff7a1a"/>
          </linearGradient>
        </defs>
        <path d="M24 4l-3 22 3 4 3-4-3-22z" fill="url(#bl)"/>
        <rect x="22.4" y="26" width="3.2" height="9" rx="1" fill="#9fbbe0"/>
        <rect x="17" y="30" width="14" height="3" rx="1.5" fill="#7da3cf"/>
        <path d="M24 35c4 3 7 5 7 8 0 0-3-1-7-1s-7 1-7 1c0-3 3-5 7-8z" fill="url(#fl)"/>
      </svg>
    </div>
    <div class="brand">
      <span class="game">TaskBar Hero</span>
      <span class="name">RESTBAR HERO</span>
    </div>
    <div class="spacer"></div>
    <span class="handle"><b>@RestBarHero</b></span>
    <span class="live"><span class="dot"></span>Ao Vivo</span>
  </header>

  <!-- LEAD -->
  <section class="lead">
    <div class="eyebrow">Calculadora de Loot • Baú Azul</div>
    <h1>Qual a sua chance no <span class="blue">Stage Boss Box</span>?</h1>
    <p>Ajuste o seu <strong>Bônus de Drop</strong> abaixo e veja na hora a chance final de dropar o baú azul nos chefes de Level&nbsp;65 e Level&nbsp;80.</p>
  </section>

  <!-- CONTROL PANEL -->
  <section class="panel">
    <div class="panel-head">
      <span class="label">⚡ Bônus de Drop</span>
      <span class="hint">é a única coisa que você ajusta</span>
    </div>

    <div class="bonus-readout">
      <span id="bonusBig">500</span><span class="pct">%</span>
    </div>

    <div class="slider-row">
      <input id="bonusRange" type="range" min="0" max="2000" step="5" value="500" aria-label="Bônus de drop em porcentagem">
      <div class="num-wrap">
        <input id="bonusInput" type="number" min="0" max="100000" step="1" value="500" aria-label="Valor exato do bônus de drop">
        <span class="sign">%</span>
      </div>
    </div>

    <div class="presets" id="presets">
      <span class="lbl">Rápido:</span>
      <button class="chip" data-v="0">0%</button>
      <button class="chip" data-v="100">100%</button>
      <button class="chip" data-v="250">250%</button>
      <button class="chip active" data-v="500">500%</button>
      <button class="chip" data-v="1000">1000%</button>
    </div>
  </section>

  <!-- TIME PANEL -->
  <section class="panel">
    <div class="panel-head">
      <span class="label">⏱️ Tempo de Fase</span>
      <span class="hint">quanto você leva pra concluir 1 fase</span>
    </div>

    <div class="bonus-readout">
      <span id="timeBig">1:30</span><span class="min">min</span>
    </div>

    <div class="slider-row">
      <input id="timeRange" class="blue" type="range" min="20" max="600" step="5" value="90" aria-label="Tempo de fase em segundos">
      <div class="num-wrap">
        <input id="timeInput" type="text" inputmode="numeric" value="1:30" aria-label="Tempo de fase (mm:ss)">
        <span class="sign" style="color:var(--rare)">m:s</span>
      </div>
    </div>

    <div class="presets" id="timePresets">
      <span class="lbl">Rápido:</span>
      <button class="chip blue" data-s="75">1:15</button>
      <button class="chip blue active" data-s="90">1:30</button>
      <button class="chip blue" data-s="120">2:00</button>
      <button class="chip blue" data-s="150">2:30</button>
      <button class="chip blue" data-s="180">3:00</button>
    </div>

    <!-- VERDICT -->
    <div class="verdict" id="verdict">
      <div class="verdict-top">
        <div class="vc-swatch"></div>
        <div class="vc-text">
          <span class="vc-rank" id="vcRank">Perfeito</span>
          <span class="vc-note" id="vcNote">Buffer ideal: pega o baú sem desperdiçar tempo.</span>
        </div>
        <div class="vc-cycle">
          <span class="lab">Próxima chance de baú</span><br>
          <span class="val" id="vcCycle">7:30</span>
        </div>
      </div>
      <div class="vc-stats">
        <div class="vc-stat"><div class="k">Fases p/ baú</div><div class="v" id="vcStages">5</div></div>
        <div class="vc-stat"><div class="k">Folga <small>(ideal +4s)</small></div><div class="v" id="vcWaste">+0:30</div></div>
        <div class="vc-stat"><div class="k">Caixas / hora</div><div class="v" id="vcRate">8,0</div></div>
      </div>
      <div class="eff-wrap">
        <div class="eff-head"><span>Eficiência do farm <small>(teto = 1 baú a cada 6:00)</small></span><b id="vcEff">93%</b></div>
        <div class="eff-bar"><span id="vcEffBar"></span></div>
      </div>
    </div>
  </section>

  <!-- LOOT CARDS -->
  <p class="cards-intro">Cada ciclo te dá <b>1 caixa</b>. A <b>chance final</b> decide quantas dessas caixas vêm <span class="blue-t">azuis</span> — por isso o número que importa é <b>baús azuis / hora</b> (caixas/hora × chance).</p>
  <section class="grid" id="cards"></section>

  <!-- RECOMMENDATIONS -->
  <section class="reco">
    <h2>🎯 <span class="em">Melhor tempo de fase</span> pra farmar</h2>
    <p class="desc">Cada alvo fecha o ciclo com <b>~4s de folga</b> depois dos 6:00 — quase no máximo de baús/hora, mas com margem pra <b>não perder o baú por delay/lag</b>. Os números de baús azuis/h abaixo já usam a <b>sua chance cadastrada</b>. ⚠️ Fique <b>nesse tempo ou um pouco acima</b>: ficar abaixo te joga pra próxima faixa de fases e derruba a eficiência.</p>
    <div class="reco-grid" id="recoGrid"></div>
    <p class="reco-summary" id="recoSummary"></p>
    <div class="legend" id="legend"></div>
  </section>

  <!-- FOOTER -->
  <footer class="foot">
    <span class="formula">Fórmula: <code>Final = Base × (1 + Bônus ÷ 100)</code></span>
    <nav class="media" aria-label="Mídias do canal">
      <a class="medbtn yt" href="https://www.youtube.com/@RestBarHero" target="_blank" rel="noopener">
        <svg viewBox="0 0 24 24" aria-hidden="true"><path d="M23 7.5a3 3 0 0 0-2.1-2.1C19 5 12 5 12 5s-7 0-8.9.4A3 3 0 0 0 1 7.5 31 31 0 0 0 .6 12 31 31 0 0 0 1 16.5a3 3 0 0 0 2.1 2.1C5 19 12 19 12 19s7 0 8.9-.4a3 3 0 0 0 2.1-2.1A31 31 0 0 0 23.4 12 31 31 0 0 0 23 7.5zM9.8 15.2V8.8l5.5 3.2-5.5 3.2z" fill="currentColor"/></svg>
        <span>@RestBarHero</span>
      </a>
      <a class="medbtn dc" href="https://discord.com/invite/PGZyVW9D" target="_blank" rel="noopener">
        <svg viewBox="0 0 24 24" aria-hidden="true"><path d="M20 4.5A18 18 0 0 0 15.5 3l-.3.5a14 14 0 0 1 4 1.9 16 16 0 0 0-13 0 14 14 0 0 1 4-1.9L9.8 3A18 18 0 0 0 5.3 4.5 19 19 0 0 0 2 17.4a18 18 0 0 0 5.4 2.7l.6-1a12 12 0 0 1-1.9-.9l.5-.4a13 13 0 0 0 11 0l.5.4a12 12 0 0 1-1.9.9l.6 1A18 18 0 0 0 23 17.4 19 19 0 0 0 20 4.5zM9.3 14.6c-.9 0-1.6-.8-1.6-1.8s.7-1.8 1.6-1.8 1.6.8 1.6 1.8-.7 1.8-1.6 1.8zm5.4 0c-.9 0-1.6-.8-1.6-1.8s.7-1.8 1.6-1.8 1.6.8 1.6 1.8-.7 1.8-1.6 1.8z" fill="currentColor"/></svg>
        <span>Discord</span>
      </a>
    </nav>
  </footer>

</div>

<script>
  // --- Dados dos baús (vindos da planilha) ---
  const BOXES = [
    { lvl:"Level 65", name:"Stage Boss Box Lv65", id:"#920651", base:10 },
    { lvl:"Level 80", name:"Stage Boss Box Lv80", id:"#920801", base:8  },
  ];

  const fmt = n => n.toLocaleString('pt-BR',{minimumFractionDigits:2, maximumFractionDigits:2});

  // SVG do baú pixelado azul (estilo item TBH)
  const chestSVG = `
  <svg viewBox="0 0 32 32" shape-rendering="crispEdges" xmlns="http://www.w3.org/2000/svg" aria-hidden="true">
    <rect x="5"  y="6"  width="22" height="7" fill="#3f7fd6"/>
    <rect x="5"  y="6"  width="22" height="2" fill="#6fa8ef"/>
    <rect x="5"  y="13" width="22" height="2" fill="#1c3f76"/>
    <rect x="4"  y="15" width="24" height="11" fill="#2f63b4"/>
    <rect x="4"  y="15" width="24" height="2" fill="#4f86d6"/>
    <rect x="4"  y="24" width="24" height="2" fill="#163763"/>
    <rect x="14" y="11" width="4"  height="9" fill="#ffd76a"/>
    <rect x="14" y="11" width="4"  height="2" fill="#fff0bf"/>
    <rect x="15" y="16" width="2"  height="3" fill="#b8861f"/>
    <rect x="4"  y="14" width="2"  height="12" fill="#6fa8ef"/>
    <rect x="26" y="14" width="2"  height="12" fill="#6fa8ef"/>
  </svg>`;

  // Monta os cards
  const cardsEl = document.getElementById('cards');
  cardsEl.innerHTML = BOXES.map((b,i)=>`
    <article class="loot" id="loot${i}" style="--glow:.25">
      <div class="loot-head">
        <span class="rare-tag">◆ Rare</span>
        <span class="item-id">${b.id}</span>
      </div>
      <div class="chest-row">
        <div class="chest">${chestSVG}</div>
        <div>
          <div class="title">${b.name}</div>
          <div class="sub">Chefe • ${b.lvl}</div>
        </div>
      </div>
      <div class="stat-line">
        <span class="k">Chance Base</span>
        <span class="v">${fmt(b.base)}%</span>
      </div>
      <div class="final">
        <div class="k">Chance Final de Drop</div>
        <div class="big"><span class="num" id="final${i}">0,00</span><span class="u">%</span></div>
      </div>
      <div class="bar"><span id="fill${i}"></span></div>
      <div class="cap-note" id="cap${i}"></div>
      <div class="perhour">
        <span class="k">Baús azuis / hora</span>
        <span class="v"><span id="bph${i}">0,0</span> <small>baús/h</small></span>
      </div>
    </article>
  `).join('');

  // ===== Controles & estado =====
  const COOLDOWN = 360; // 6:00 em segundos

  const range = document.getElementById('bonusRange');
  const input = document.getElementById('bonusInput');
  const big   = document.getElementById('bonusBig');
  const bonusChips = [...document.querySelectorAll('#presets .chip')];

  const tRange = document.getElementById('timeRange');
  const tInput = document.getElementById('timeInput');
  const tBig   = document.getElementById('timeBig');
  const timeChips = [...document.querySelectorAll('#timePresets .chip')];

  let state = { bonus:500, secs:90 };

  const clampNonNeg = v => { v = parseFloat(v); return isNaN(v)||v<0 ? 0 : v; };
  const mmss = s => { s=Math.round(s); return Math.floor(s/60)+':'+String(s%60).padStart(2,'0'); };
  const parseTime = txt => {
    txt = String(txt).trim();
    if(txt.includes(':')){ const [m,s]=txt.split(':'); return (parseInt(m)||0)*60 + (parseInt(s)||0); }
    return parseInt(txt)||0; // só número = segundos
  };

  // Classificação: precisa de FOLGA mínima de 4s (delay/lag) + alta eficiência.
  // Cravar exatamente em 6:00 rende o máximo, mas sem folga você perde o baú.
  const SAFE = 4; // segundos de folga recomendados
  function rate(over, eff){
    if(over < SAFE) return {rank:'Sem folga',     color:'#e0801b', note:'Você fecha quase em cima dos 6:00. Mire ~4s a mais pra não perder o baú por delay/lag.'};
    if(eff >= 95)   return {rank:'Perfeito',      color:'#2f9e44', note:'Folga segura e quase no teto de baús/hora. É isso aí.'};
    if(eff >= 88)   return {rank:'Ótimo',         color:'#74b816', note:'Farm muito bom, bem coladinho no teto.'};
    if(eff >= 80)   return {rank:'Bom',           color:'#e6a817', note:'Dá pra arrancar mais baús/hora apertando o tempo de fase.'};
    if(eff >= 70)   return {rank:'Pode melhorar', color:'#d35400', note:'Está sobrando bastante tempo entre os baús.'};
    return                 {rank:'Ineficiente',   color:'#c0392b', note:'Muito tempo perdido por ciclo — reduza o tempo de fase.'};
  }

  // ===== Recalcula tudo =====
  function recompute(){
    const { bonus, secs } = state;

    // -- BÔNUS / readout --
    big.textContent = bonus.toLocaleString('pt-BR');
    range.style.setProperty('--fill', Math.min(bonus/2000*100,100)+'%');
    bonusChips.forEach(c=>c.classList.toggle('active', parseFloat(c.dataset.v)===bonus));

    // -- TEMPO / readout --
    tBig.textContent = mmss(secs);
    tRange.style.setProperty('--fill', Math.min((secs-20)/(600-20)*100,100)+'%');
    timeChips.forEach(c=>c.classList.toggle('active', parseInt(c.dataset.s)===secs));

    // -- Mecânica do baú --
    const stages   = Math.max(1, Math.ceil(COOLDOWN / secs)); // fases necessárias
    const cycle    = stages * secs;                            // próxima chance de baú (s)
    const over     = cycle - COOLDOWN;                         // tempo perdido (s)
    const rate1h   = 3600 / cycle;                             // CAIXAS por hora (throughput)
    const eff      = COOLDOWN / cycle * 100;                   // eficiência %
    const r        = rate(over, eff);

    // -- Verdict card --
    const vd = document.getElementById('verdict');
    vd.style.setProperty('--vc', r.color);
    document.getElementById('vcRank').textContent  = r.rank;
    document.getElementById('vcNote').textContent  = r.note;
    document.getElementById('vcCycle').textContent = mmss(cycle);
    document.getElementById('vcStages').textContent= stages;
    document.getElementById('vcWaste').textContent = (over>0?'+':'') + mmss(over);
    document.getElementById('vcRate').textContent  = rate1h.toLocaleString('pt-BR',{minimumFractionDigits:1,maximumFractionDigits:1});
    document.getElementById('vcEff').textContent   = Math.round(eff)+'%';
    document.getElementById('vcEffBar').style.width = Math.min(eff,100)+'%';

    // -- Loot cards: chance final + baús azuis/hora --
    BOXES.forEach((b,i)=>{
      const final = b.base * (1 + bonus/100);
      const finalCapped = Math.min(final,100);       // chance não passa de 100% pro cálculo
      const bluePerHour = rate1h * finalCapped/100;  // baús azuis por hora

      document.getElementById('final'+i).textContent = fmt(final);
      document.getElementById('fill'+i).style.width = finalCapped+'%';
      document.getElementById('bph'+i).textContent =
        bluePerHour.toLocaleString('pt-BR',{minimumFractionDigits:1,maximumFractionDigits:1});

      const glow = (0.15 + finalCapped/100*0.85).toFixed(3);
      document.getElementById('loot'+i).style.setProperty('--glow', glow);

      const cap = document.getElementById('cap'+i);
      if(final >= 100) cap.textContent = "Garantido — passou de 100%, todo baú vem azul!";
      else if(final >= 75) cap.textContent = "Chance altíssima 🔥";
      else cap.textContent = "";
    });

    renderReco(stages);
  }

  // ===== Melhor tempo: alvo = (COOLDOWN+4s)/n, com baús azuis/h pela chance cadastrada =====
  function renderReco(currentStages){
    const grid = document.getElementById('recoGrid');
    const { bonus } = state;

    if(grid.dataset.built !== '1'){
      let html = '';
      for(let n=7; n>=2; n--){
        const target = Math.ceil((COOLDOWN + SAFE) / n); // garante >=4s de folga
        const cyc = n * target;
        html += `<div class="reco-card" data-n="${n}" data-cycle="${cyc}">
          <div class="n">${n} fases · folga +${cyc-COOLDOWN}s</div>
          <div class="t">${mmss(target)}</div>
          <div class="azuis">
            ${BOXES.map((b,i)=>`<span class="az"><i></i>${b.lvl.replace('Level ','Lv ')} <b data-i="${i}">–</b>/h</span>`).join('')}
          </div>
        </div>`;
      }
      grid.innerHTML = html;
      grid.dataset.built = '1';
    }

    // Atualiza baús azuis/hora de cada alvo conforme a chance cadastrada (bônus atual)
    [...grid.children].forEach(el=>{
      const cyc = parseFloat(el.dataset.cycle), rate1h = 3600 / cyc;
      el.querySelectorAll('b[data-i]').forEach(bEl=>{
        const i = +bEl.dataset.i;
        const final = Math.min(BOXES[i].base * (1 + bonus/100), 100);
        bEl.textContent = (rate1h * final/100).toLocaleString('pt-BR',{minimumFractionDigits:1,maximumFractionDigits:1});
      });
      el.classList.toggle('hit', parseInt(el.dataset.n)===currentStages);
    });

    // Resumo: rendimento no tempo ideal (ciclo de referência = 7:04)
    const refRate = 3600 / (COOLDOWN + SAFE);
    const az = i => (refRate * Math.min(BOXES[i].base*(1+bonus/100),100)/100)
                      .toLocaleString('pt-BR',{minimumFractionDigits:1,maximumFractionDigits:1});
    document.getElementById('recoSummary').innerHTML =
      `Com bônus de <b>${bonus.toLocaleString('pt-BR')}%</b>, no tempo ideal você tira cerca de ` +
      `<b>${az(0)}</b> baús azuis/h no ${BOXES[0].lvl} e <b>${az(1)}</b>/h no ${BOXES[1].lvl}. ` +
      `Qualquer um dos tempos acima rende praticamente o mesmo — escolha pela sua velocidade de clear.`;
  }

  // ===== Legenda de cores =====
  (function(){
    const items = [
      ['#2f9e44','Perfeito'],['#74b816','Ótimo'],['#e6a817','Bom'],
      ['#d35400','Pode melhorar'],['#c0392b','Ineficiente'],['#e0801b','Sem folga (arriscado)']
    ];
    document.getElementById('legend').innerHTML = items.map(([c,t])=>
      `<span class="it"><span class="sw" style="background:${c}"></span>${t}</span>`).join('');
  })();

  // ===== Setters =====
  function setBonus(v, from){
    state.bonus = clampNonNeg(v);
    if(from!=='range') range.value = Math.min(state.bonus,2000);
    if(from!=='input') input.value = state.bonus;
    recompute();
  }
  function setTime(secs, from){
    secs = Math.max(1, Math.round(secs));
    state.secs = secs;
    if(from!=='range') tRange.value = Math.min(Math.max(secs,20),600);
    if(from!=='input') tInput.value = mmss(secs);
    recompute();
  }

  range.addEventListener('input', e=> setBonus(e.target.value,'range'));
  input.addEventListener('input', e=> setBonus(e.target.value,'input'));
  bonusChips.forEach(c=> c.addEventListener('click', ()=> setBonus(c.dataset.v,'chip')));

  tRange.addEventListener('input', e=> setTime(parseFloat(e.target.value),'range'));
  tInput.addEventListener('change', e=> setTime(parseTime(e.target.value),'input'));
  tInput.addEventListener('blur',   e=> setTime(parseTime(e.target.value),'input'));
  timeChips.forEach(c=> c.addEventListener('click', ()=> setTime(parseInt(c.dataset.s),'chip')));

  // estado inicial
  setBonus(500,'init');
  setTime(90,'init');
</script>
</body>
</html>
