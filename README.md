<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>Sopaan · Squares and Square Roots</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Fraunces:opsz,wght@9..144,500;9..144,700&family=Source+Sans+3:wght@400;600;700&family=IBM+Plex+Mono:wght@500;600&display=swap">
<style>
  html,body{margin:0;} img{max-width:100%;} [hidden]{display:none !important;}
  :root{
    --navy:#16264A; --navy-2:#1F3B6B; --gold:#C79A3E; --gold-soft:#F3E7C9;
    --paper:#FBF9F4; --paper-2:#F1EAD8; --card:#FFFFFF;
    --ink:#211E1A; --ink-soft:#655D4C; --rule:#E4DCC8;
    --success:#2E8B57; --success-soft:#E1F2E7;
    --danger:#BF4B45; --danger-soft:#FAE3E1;
    --locked:#C7BEA9;
    --focus:#1F3B6B;
    --accent-text:#1F3B6B; --retry-text:#8A661F;
    color-scheme:light;
  }
  @media (prefers-color-scheme: dark){
    :root:not([data-theme="light"]){
      --navy:#0E1830; --navy-2:#16264A; --gold:#E0B75B; --gold-soft:#3A2F16;
      --paper:#141210; --paper-2:#1C1914; --card:#1C1914;
      --ink:#EDE7DA; --ink-soft:#B2A996; --rule:#3A342A;
      --success:#7BC79A; --success-soft:#1B2E22;
      --danger:#E38884; --danger-soft:#331D1B;
      --locked:#4A4436;
      --focus:#E0B75B;
      --accent-text:#E0B75B; --retry-text:#E0B75B;
      color-scheme:dark;
    }
  }
  :root[data-theme="dark"]{
    --navy:#0E1830; --navy-2:#16264A; --gold:#E0B75B; --gold-soft:#3A2F16;
    --paper:#141210; --paper-2:#1C1914; --card:#1C1914;
    --ink:#EDE7DA; --ink-soft:#B2A996; --rule:#3A342A;
    --success:#7BC79A; --success-soft:#1B2E22;
    --danger:#E38884; --danger-soft:#331D1B;
    --locked:#4A4436;
    --focus:#E0B75B;
    --accent-text:#E0B75B; --retry-text:#E0B75B;
    color-scheme:dark;
  }

  *{box-sizing:border-box;}
  body{background:var(--paper); color:var(--ink); font-family:'Source Sans 3',-apple-system,'Segoe UI',sans-serif; padding-inline:0; padding-block:0;}
  h1,h2,h3{font-family:'Fraunces',Georgia,serif; text-wrap:balance; margin:0;}
  .num{font-family:'IBM Plex Mono',ui-monospace,monospace; font-variant-numeric:tabular-nums;}

  header.brand{
    background:linear-gradient(155deg,var(--navy) 0%, var(--navy-2) 100%);
    color:#F4EFDF; padding-block:calc(20px + env(safe-area-inset-top,0px)) 18px; padding-inline:20px;
  }
  .brand-row{display:flex; align-items:center; gap:12px; max-width:900px; margin:0 auto;}
  .crest{
    width:42px; height:42px; border-radius:10px; background:var(--gold); color:var(--navy);
    display:flex; align-items:center; justify-content:center; font-family:'Fraunces',serif; font-weight:700; font-size:18px; flex-shrink:0;
  }
  .brand-name{font-size:12px; letter-spacing:.08em; text-transform:uppercase; color:var(--gold); font-weight:700;}
  .series-name{font-size:19px; font-weight:700; font-family:'Fraunces',serif;}
  .chapter-eyebrow{max-width:900px; margin:14px auto 0; font-size:12px; letter-spacing:.06em; text-transform:uppercase; color:#AEB9D6;}
  .chapter-title{font-size:28px; max-width:900px; margin:2px auto 0;}
  .chapter-sub{font-size:14.5px; color:var(--gold); font-weight:700; max-width:900px; margin:3px auto 0;}

  .chapter-progress{max-width:900px; margin:14px auto 0; display:flex; align-items:center; gap:10px;}
  .cp-track{flex:1; height:6px; border-radius:99px; background:rgba(255,255,255,.18); overflow:hidden;}
  .cp-fill{height:100%; background:var(--gold); border-radius:99px; transition:width .3s ease;}
  .cp-label{font-size:11.5px; color:#CFD7EA; white-space:nowrap;}

  .tabbar{position:sticky; top:env(safe-area-inset-top,0px); z-index:15; background:var(--paper); border-bottom:1px solid var(--rule); overflow-x:auto; white-space:nowrap;}
  .tabbar-inner{max-width:900px; margin:0 auto; display:flex; padding-inline:16px;}
  .tab-btn{font-family:inherit; font-size:14px; font-weight:600; color:var(--ink-soft); background:none; border:none; padding:13px 16px; cursor:pointer; position:relative; flex-shrink:0;}
  .tab-btn.active{color:var(--accent-text);}
  .tab-btn.active::after{content:''; position:absolute; left:12px; right:12px; bottom:0; height:3px; background:var(--gold); border-radius:3px 3px 0 0;}
  .tab-count{font-size:11px; color:var(--ink-soft); margin-left:5px;}

  .slide-progress{max-width:900px; margin:0 auto; padding:10px 16px 0; display:flex; align-items:center; gap:10px;}
  .sp-track{flex:1; height:5px; border-radius:99px; background:var(--rule); overflow:hidden;}
  .sp-fill{height:100%; background:var(--accent-text); border-radius:99px; transition:width .3s ease;}
  .sp-label{font-size:12px; color:var(--ink-soft); white-space:nowrap; font-weight:600;}

  .wrap{max-width:900px; margin:0 auto; padding:16px 16px calc(110px + env(safe-area-inset-bottom,0px));}

  .qcard{background:var(--card); border:1px solid var(--rule); border-radius:14px; padding:18px;}
  .qhead{display:flex; align-items:flex-start; gap:10px; margin-bottom:10px;}
  .qnum{width:32px; height:32px; border-radius:8px; background:var(--gold-soft); color:var(--accent-text); display:flex; align-items:center; justify-content:center; font-weight:700; font-family:'Fraunces',serif; flex-shrink:0; font-size:14px;}
  .qtext{font-size:16px; line-height:1.55; flex:1;}
  .qtag{font-size:10.5px; color:var(--gold); background:var(--gold-soft); padding:2px 7px; border-radius:99px; font-weight:700; margin-left:6px; white-space:nowrap;}
  .marks-pill{font-size:11px; font-weight:700; color:var(--ink-soft); border:1px solid var(--rule); padding:3px 9px; border-radius:99px; margin-left:auto; flex-shrink:0; white-space:nowrap;}
  .step-badge{font-size:11px; font-weight:700; color:var(--accent-text); background:var(--paper-2); border:1px solid var(--rule); padding:3px 9px; border-radius:99px; display:inline-block; margin-bottom:12px;}

  .options{display:flex; flex-direction:column; gap:8px; margin-top:10px;}
  .opt{display:flex; align-items:center; gap:10px; padding:11px 12px; border:1.5px solid var(--rule); border-radius:10px; cursor:pointer; font-size:15px; background:var(--paper);}
  .opt input{accent-color:var(--navy-2);}
  .opt.is-correct{border-color:var(--success); background:var(--success-soft);}
  .opt.is-wrong{border-color:var(--danger); background:var(--danger-soft);}
  .opt.locked{cursor:not-allowed;}

  .subpart-label{font-weight:700; font-size:12.5px; color:var(--accent-text); text-transform:uppercase; letter-spacing:.03em; margin:14px 0 6px;}
  .or-divider{text-align:center; font-size:11px; font-weight:700; letter-spacing:.08em; color:var(--ink-soft); margin:8px 0;}

  .steps{display:flex; flex-direction:column; gap:10px;}
  .step-line{font-size:14.5px; line-height:1.9; background:var(--paper); border:1px dashed var(--rule); border-radius:10px; padding:9px 12px;}
  .step-line.resolved{opacity:.9;}
  .blank-input{font-family:'IBM Plex Mono',monospace; font-size:14px; border:1.5px solid var(--rule); border-radius:6px; padding:3px 8px; width:120px; background:var(--card); color:var(--ink); margin:0 2px;}
  .blank-input:focus{outline:none; border-color:var(--focus); box-shadow:0 0 0 3px var(--gold-soft);}
  .blank-input.is-correct{border-color:var(--success); background:var(--success-soft);}
  .blank-input.is-wrong{border-color:var(--danger); background:var(--danger-soft);}
  .blank-input[disabled]{opacity:.85;}
  .reveal-note{font-size:12px; color:var(--danger); padding-left:2px; margin-top:-2px;}

  .feedback{font-size:13.5px; padding:10px 12px; border-radius:9px; margin-top:14px; display:none;}
  .feedback.show{display:block;}
  .feedback.ok{background:var(--success-soft); color:var(--success);}
  .feedback.retry{background:var(--gold-soft); color:var(--retry-text);}
  .feedback.reveal{background:var(--danger-soft); color:var(--danger);}
  .feedback.err{background:var(--danger-soft); color:var(--danger);}
  .attempts-dots{display:inline-flex; gap:4px; margin-left:2px;}
  .attempts-dots span{width:6px; height:6px; border-radius:50%; background:var(--ink-soft); opacity:.3; display:inline-block;}
  .attempts-dots span.used{opacity:1; background:var(--danger);}

  .ar-box{background:var(--paper-2); border-radius:10px; padding:10px 12px; margin-bottom:12px; font-size:13px; color:var(--ink-soft);}

  .navbar{
    position:fixed; left:0; right:0; bottom:0; z-index:30; background:var(--paper);
    border-top:1px solid var(--rule); padding:10px 16px calc(10px + env(safe-area-inset-bottom,0px));
  }
  .navbar-inner{max-width:900px; margin:0 auto; display:flex; gap:8px; flex-wrap:wrap; align-items:center;}
  .btn{font-family:inherit; font-size:13.5px; font-weight:700; padding:10px 14px; border-radius:9px; border:1.5px solid var(--rule); background:var(--card); color:var(--ink); cursor:pointer;}
  .btn:hover{border-color:var(--navy-2);}
  .btn:disabled{opacity:.4; cursor:not-allowed;}
  .btn-primary{background:var(--navy-2); color:#fff; border-color:var(--navy-2);}
  .navbar .spacer{flex:1;}

  .fab{position:fixed; right:16px; bottom:calc(74px + env(safe-area-inset-bottom,0px)); background:var(--gold); color:var(--navy); border:none; border-radius:999px; padding:11px 16px; font-family:inherit; font-weight:700; font-size:13px; display:flex; align-items:center; gap:7px; cursor:pointer; box-shadow:0 6px 16px rgba(0,0,0,.18); z-index:35;}
  .fab-badge{background:rgba(255,255,255,.55); border-radius:99px; padding:1px 7px; font-size:11px;}

  .overlay{position:fixed; inset:0; background:rgba(20,18,14,.45); z-index:50; display:none; align-items:flex-end; justify-content:center;}
  .overlay.show{display:flex;}
  .palette{background:var(--card); width:min(480px,100%); max-height:78vh; overflow-y:auto; border-radius:18px 18px 0 0; padding:18px 18px calc(18px + env(safe-area-inset-bottom,0px)); border:1px solid var(--rule); border-bottom:none;}
  @media (min-width:640px){ .overlay{align-items:center;} .palette{border-radius:18px; border-bottom:1px solid var(--rule); max-height:74vh;} }
  .palette-head{display:flex; align-items:center; justify-content:space-between; margin-bottom:6px;}
  .palette-head h2{font-size:16px;}
  .palette-close{background:none; border:none; font-size:20px; color:var(--ink-soft); cursor:pointer; padding:4px;}
  .palette-legend{display:flex; gap:12px; flex-wrap:wrap; font-size:11px; color:var(--ink-soft); margin:10px 0 14px;}
  .palette-legend span{display:inline-flex; align-items:center; gap:5px;}
  .dot{width:9px; height:9px; border-radius:50%; display:inline-block;}
  .dot.correct{background:var(--success);} .dot.revealed{background:var(--danger);}
  .dot.skipped{background:var(--gold);} .dot.locked{background:var(--locked);}
  .dot.current{background:var(--navy-2);}
  .chip-grid{display:grid; grid-template-columns:repeat(auto-fill,minmax(48px,1fr)); gap:8px;}
  .chip{border:1.5px solid var(--rule); border-radius:9px; padding:8px 4px; text-align:center; font-family:'IBM Plex Mono',monospace; font-size:12.5px; font-weight:600; cursor:pointer; background:var(--paper); color:var(--ink);}
  .chip[data-status="correct"]{border-color:var(--success); background:var(--success-soft); color:var(--success);}
  .chip[data-status="revealed"]{border-color:var(--danger); background:var(--danger-soft); color:var(--danger);}
  .chip[data-status="skipped"]{border-color:var(--gold); background:var(--gold-soft); color:var(--retry-text);}
  .chip[data-status="locked"]{border-color:var(--rule); color:var(--locked); cursor:not-allowed; background:var(--paper-2);}
  .chip[data-status="current"]{outline:2px solid var(--navy-2); outline-offset:1px;}

  .toast{position:fixed; left:50%; bottom:calc(140px + env(safe-area-inset-bottom,0px)); transform:translateX(-50%); background:var(--ink); color:var(--paper); padding:9px 16px; border-radius:99px; font-size:13px; opacity:0; pointer-events:none; transition:opacity .25s ease; z-index:60;}
  .toast.show{opacity:1;}

  .done-card{text-align:center; padding:36px 20px;}
  .done-card .big{font-size:38px; margin-bottom:6px;}
  .score-pills{display:flex; gap:10px; justify-content:center; flex-wrap:wrap; margin:16px 0;}
  .score-pill{padding:8px 16px; border-radius:99px; font-size:13px; font-weight:700;}

  footer.brandfoot{max-width:900px; margin:14px auto 0; padding:0 16px calc(110px + env(safe-area-inset-bottom,0px)); text-align:center; font-size:12px; color:var(--ink-soft);}

  .mode-pill{font-family:inherit; font-size:12.5px; font-weight:700; color:var(--navy); background:var(--gold); border:none; border-radius:99px; padding:6px 14px; cursor:pointer; margin-top:12px; display:inline-flex; align-items:center; gap:6px;}
  .mode-pick{display:flex; flex-direction:column; gap:14px; padding:8px 0 24px;}
  .mode-card{background:var(--card); border:1.5px solid var(--rule); border-radius:16px; padding:22px; cursor:pointer; text-align:left;}
  .mode-card:hover{border-color:var(--navy-2);}
  .mode-card .mode-icon{font-size:26px; margin-bottom:8px;}
  .mode-card h3{font-size:18px; margin-bottom:6px;}
  .mode-card p{font-size:13.5px; color:var(--ink-soft); line-height:1.5; margin:0;}
  .quiz-hint{font-size:12.5px; color:var(--ink-soft); background:var(--paper-2); border-radius:9px; padding:8px 12px; margin-bottom:14px;}
  .review-row{border:1px solid var(--rule); border-radius:10px; padding:11px 13px; margin-bottom:10px;}
  .review-tag{font-size:11.5px; font-weight:700; margin-bottom:4px; display:block;}
  .review-tag.ok{color:var(--success);} .review-tag.bad{color:var(--danger);} .review-tag.na{color:var(--ink-soft);}
  .review-q{font-size:13.5px; margin-bottom:6px; color:var(--ink-soft);}
  .review-ans{font-size:13px; margin-bottom:2px;}

  .who-row{max-width:900px; margin:12px auto 0; display:flex; flex-wrap:wrap; gap:8px; align-items:center;}
  .who-row .mode-pill{margin-top:0;}
  .who{display:inline-flex; flex-wrap:wrap; align-items:center; gap:6px; font-size:12.5px; color:#CFD7EA;}
  .who b{color:#F4EFDF;}
  .who button{font-family:inherit; font-size:12px; font-weight:700; color:#F4EFDF; background:rgba(255,255,255,.12); border:1px solid rgba(255,255,255,.22); border-radius:99px; padding:5px 11px; cursor:pointer;}
  .who button:hover{background:rgba(255,255,255,.2);}
  .login-card{max-width:460px; margin:8px auto 0; background:var(--card); border:1px solid var(--rule); border-radius:16px; padding:22px;}
  .login-card h2{font-size:21px; margin-bottom:4px;}
  .login-card p.lead{font-size:13.5px; color:var(--ink-soft); margin:0 0 16px; line-height:1.5;}
  .fld{display:flex; flex-direction:column; gap:5px; margin-bottom:12px;}
  .fld label{font-size:12px; font-weight:700; letter-spacing:.04em; text-transform:uppercase; color:var(--ink-soft);}
  .fld input{font-family:inherit; font-size:15px; padding:10px 12px; border:1.5px solid var(--rule); border-radius:9px; background:var(--paper); color:var(--ink);}
  .fld input:focus{outline:none; border-color:var(--focus); box-shadow:0 0 0 3px var(--gold-soft);}
  .fld-row{display:grid; grid-template-columns:1fr 1fr; gap:10px;}
  .login-err{font-size:13px; color:var(--danger); background:var(--danger-soft); border-radius:8px; padding:8px 10px; margin-bottom:12px;}
  .login-note{font-size:12px; color:var(--ink-soft); margin-top:12px; line-height:1.5;}
  .known{margin:0 0 16px; display:flex; flex-direction:column; gap:6px;}
  .known-label{font-size:12px; font-weight:700; letter-spacing:.04em; text-transform:uppercase; color:var(--ink-soft);}
  .known-btn{display:flex; justify-content:space-between; align-items:center; gap:10px; text-align:left; font-family:inherit; font-size:14.5px; padding:10px 12px; border:1.5px solid var(--rule); border-radius:10px; background:var(--paper); color:var(--ink); cursor:pointer;}
  .known-btn:hover{border-color:var(--navy-2);}
  .known-btn small{font-size:12px; color:var(--ink-soft);}
  .rec-card{background:var(--card); border:1px solid var(--rule); border-radius:14px; padding:18px; margin-bottom:14px;}
  .rec-card h2{font-size:19px; margin-bottom:10px;}
  .rec-card h3{font-size:15px; margin:4px 0 8px;}
  .rec-table-wrap{overflow-x:auto;}
  .rec-table{width:100%; border-collapse:collapse; font-size:13.5px; font-variant-numeric:tabular-nums;}
  .rec-table th{text-align:left; font-size:11.5px; text-transform:uppercase; letter-spacing:.04em; color:var(--ink-soft); padding:6px 8px; border-bottom:1px solid var(--rule); white-space:nowrap;}
  .rec-table td{padding:8px; border-bottom:1px solid var(--rule); white-space:nowrap;}
  .rec-bar{display:inline-block; width:70px; height:6px; border-radius:99px; background:var(--rule); overflow:hidden; vertical-align:middle; margin-right:6px;}
  .rec-bar i{display:block; height:100%; background:var(--success);}
  .rec-empty{font-size:13.5px; color:var(--ink-soft);}
  .sec-sub{max-width:900px; margin:0 auto; padding:10px 16px 0; font-size:12.5px; font-weight:700; color:var(--accent-text); letter-spacing:.02em;}
  .opt{flex-wrap:wrap;}
  .opt-l{font-family:'IBM Plex Mono',monospace; font-size:13px; font-weight:600; color:var(--ink-soft);}
  .opt-t{flex:1; min-width:0;}
  .opt.is-chosen:not(.is-correct):not(.is-wrong){border-color:var(--navy-2); background:var(--gold-soft);}
  .opt-tag{font-size:11px; font-weight:700; padding:2px 8px; border-radius:99px; background:var(--card); border:1px solid currentColor; white-space:nowrap;}
  .opt.is-correct .opt-tag{color:var(--success);} .opt.is-wrong .opt-tag{color:var(--danger);} .opt.is-chosen:not(.is-correct):not(.is-wrong) .opt-tag{color:var(--accent-text);}
  .chosen{font-size:13.5px; margin-top:10px; padding:8px 12px; border-radius:9px;}
  .chosen.ok{background:var(--success-soft); color:var(--success);} .chosen.bad{background:var(--danger-soft); color:var(--danger);}
  .chosen + .chosen{margin-top:6px;}
  .solution{margin-top:14px; border:1px solid var(--rule); border-left:4px solid var(--gold); background:var(--paper-2); border-radius:10px; padding:12px 14px;}
  .sol-h{font-family:'Fraunces',Georgia,serif; font-weight:700; font-size:14px; color:var(--accent-text); margin-bottom:6px;}
  .sol-line{font-size:14.5px; line-height:1.7;}
  .rev-sol summary{cursor:pointer; font-size:12.5px; font-weight:700; color:var(--accent-text); margin-top:6px;}
  .rev-sol .solution{margin-top:8px;}
  .chapter-credit{max-width:900px; margin:4px auto 0; font-size:12px; color:#CFD7EA;}
  footer.brandfoot a{color:inherit;}
  .blank-input.wide{width:260px; max-width:100%; font-family:'Source Sans 3',sans-serif;}
  .blank-input.expr{width:170px; max-width:100%;}
  /*fix-layout*/ .cp-fill,.sp-fill{width:0;} .fld{min-width:0;} .fld input{width:100%; min-width:0; box-sizing:border-box;}
  .fig{margin:6px 0 10px; display:flex; justify-content:center;}
  .figsvg{width:100%; max-width:340px; height:auto; overflow:visible;}
  .figsvg .ln,.figsvg .arm{stroke:var(--ink); stroke-width:1.6; fill:none;}
  .figsvg .arm{stroke:var(--accent-text); stroke-width:2;}
  .figsvg .pt{fill:var(--ink);}
  .figsvg .lb{fill:var(--ink); font:600 13px 'Source Sans 3',sans-serif;}
  .figsvg .al{fill:var(--accent-text); font:700 12px 'Source Sans 3',sans-serif;}
  .figsvg .wg{fill:var(--gold-soft); stroke:var(--gold); stroke-width:1.2;}
  .figsvg .wg2{fill:rgba(199,154,62,.35); stroke:var(--gold); stroke-width:1.2;}
  .figsvg .ra{fill:none; stroke:var(--ink); stroke-width:1.2;}
  .figsvg .ahd{fill:var(--ink);}
  .figsvg .pr{fill:var(--paper-2); stroke:var(--ink-soft); stroke-width:1.2;}
  .figsvg .tk{stroke:var(--ink-soft); stroke-width:.8;}
  .figsvg .po{fill:var(--ink); font:600 8.5px 'IBM Plex Mono',monospace;}
  .figsvg .pi{fill:var(--danger); font:600 7.5px 'IBM Plex Mono',monospace;}
  .figsvg .sh{fill:var(--gold-soft); stroke:var(--ink); stroke-width:1.5; stroke-linejoin:round;}
  .figsvg .sh2{fill:rgba(199,154,62,.38); stroke:var(--ink); stroke-width:1.5; stroke-linejoin:round;}
  .figsvg .sh3{fill:rgba(199,154,62,.22); stroke:var(--ink); stroke-width:1.5; stroke-linejoin:round;}
  .figsvg .none{fill:none;}
  .figsvg .hid{stroke-dasharray:5 4; fill:none;}
  .figsvg .tick{stroke:var(--ink); stroke-width:1.4; fill:none;}
  .figsvg .shd{fill:var(--accent-text); fill-opacity:.55;}
  .figsvg .cell{fill:var(--card); stroke:var(--ink); stroke-width:1.1;}
  .figsvg .dr{fill:var(--danger);} .figsvg .dw{fill:var(--card); stroke:var(--ink); stroke-width:1.2;}
  .figsvg .dotfill{fill:var(--danger);}
  .tt{border-collapse:collapse; font-size:13.5px; margin:4px auto; font-variant-numeric:tabular-nums;} .tt th,.tt td{border:1px solid var(--rule); padding:4px 9px; text-align:left;} .tt th{background:var(--paper-2); font-weight:700;} .ttw{overflow-x:auto; max-width:100%;}
  .fq{display:inline-flex; flex-direction:column; vertical-align:middle; text-align:center; font-size:.82em; line-height:1.12; margin:0 2px;}
  .fq>span:first-child{border-bottom:1.5px solid currentColor; padding:0 2px;}
  .fq>span:last-child{padding:0 2px;}
  .mx{white-space:nowrap;}
  .blank-input.fr{width:110px;}
  @media (prefers-reduced-motion:reduce){ *{transition:none !important;} }
.datline{display:block;margin-top:8px;padding:8px 10px;border-radius:8px;background:var(--paper-2);font:500 14px/1.7 'IBM Plex Mono',monospace;word-spacing:2px;overflow-wrap:anywhere;}

  .theory{display:flex;flex-direction:column;gap:16px;padding-bottom:40px;}
  .hub{display:grid;grid-template-columns:1fr;gap:12px;}
  @media (min-width:640px){ .hub{grid-template-columns:repeat(3,1fr);} }
  .hub-card{background:var(--card);border:1px solid var(--rule);border-radius:14px;padding:16px;display:flex;flex-direction:column;gap:8px;}
  .hub-card h3{font-family:'Fraunces',serif;font-size:18px;margin:0;color:var(--accent-text);}
  .hub-card p{margin:0;font-size:14px;color:var(--ink-soft);line-height:1.5;}
  .hub-btns{display:flex;flex-wrap:wrap;gap:8px;margin-top:auto;}
  .hub-btn{min-height:40px;border:1.5px solid var(--rule);background:var(--paper-2);color:var(--ink);border-radius:10px;padding:8px 12px;font:600 14px 'Source Sans 3',sans-serif;cursor:pointer;text-align:left;}
  .hub-btn:hover{border-color:var(--gold);}
  .hub-btn.primary{background:var(--navy);color:#F4EFDF;border-color:var(--navy);}
  .note{background:var(--card);border:1px solid var(--rule);border-radius:14px;padding:18px;scroll-margin-top:120px;}
  .note h2{font-family:'Fraunces',serif;font-size:22px;margin:0 0 4px;color:var(--ink);}
  .note .lt{font-size:13.5px;color:var(--ink-soft);margin:0 0 12px;}
  .note .lt b{color:var(--accent-text);}
  .note h4{font:700 15px 'Source Sans 3',sans-serif;margin:16px 0 6px;color:var(--accent-text);}
  .note p,.note li{font-size:15.5px;line-height:1.6;}
  .note ul{padding-left:20px;margin:6px 0;}
  .keybox{background:var(--gold-soft);border-left:4px solid var(--gold);border-radius:8px;padding:10px 12px;margin:10px 0;font-size:15px;line-height:1.6;}
  .keybox b{color:var(--ink);}
  .ex{background:var(--paper-2);border-radius:10px;padding:12px;margin:10px 0;}
  .ex .exh{font-family:'Fraunces',serif;font-weight:700;color:var(--accent-text);margin-bottom:4px;}
  .ex .exl{font-size:15px;line-height:1.7;}
  .ttab{width:100%;border-collapse:collapse;font-size:14.5px;margin:8px 0;}
  .ttab th,.ttab td{border:1px solid var(--rule);padding:7px 8px;text-align:left;vertical-align:top;}
  .ttab th{background:var(--paper-2);}
  .tscroll{overflow-x:auto;}
  .mono{font-family:'IBM Plex Mono',monospace;font-size:.92em;}
  @media (max-width:480px){ .ttab{font-size:13.5px;} .ttab th,.ttab td{padding:6px;} }
  .note .figsvg{max-width:100%;height:auto;display:block;margin:8px auto;}


  .rep-top{display:flex;flex-wrap:wrap;gap:18px;align-items:center;justify-content:center;margin-top:8px;}
  .rep-legend{flex:1;min-width:220px;display:flex;flex-direction:column;gap:8px;}
  .rep-cap{font:700 13px 'Source Sans 3',sans-serif;color:var(--ink-soft);text-transform:uppercase;letter-spacing:.05em;}
  .rep-li{display:flex;align-items:center;gap:6px;font-size:15px;}
  .rep-n{margin-left:auto;white-space:nowrap;padding-left:8px;font-family:'IBM Plex Mono',monospace;font-weight:600;}
  .sw{display:inline-block;width:12px;height:12px;border-radius:3px;flex:none;}
  .rep-grid{display:grid;grid-template-columns:1fr;gap:12px;}
  @media (min-width:640px){ .rep-grid{grid-template-columns:1fr 1fr;} }
  .rep-card{background:var(--card);border:1px solid var(--rule);border-radius:14px;padding:14px;display:flex;flex-direction:column;gap:10px;}
  .rep-h{display:flex;align-items:center;gap:8px;font:700 16px 'Source Sans 3',sans-serif;}
  .crit{display:inline-grid;place-items:center;width:28px;height:28px;border-radius:50%;color:var(--card);font:700 15px Fraunces,serif;flex:none;}
  .rep-row{display:flex;gap:14px;align-items:center;}
  .rep-stats{display:flex;flex-direction:column;gap:5px;font-size:14.5px;}
  .rep-stats div{display:flex;align-items:center;gap:6px;}
  .rep-lvl{margin-top:4px;color:var(--accent-text);} .rep-lvl span{color:var(--ink-soft);font-size:13px;}
  .rep-note{font-size:13px;color:var(--ink-soft);}


  .skip-chips{display:flex;flex-wrap:wrap;gap:8px;justify-content:center;margin:12px 0;}
  .skip-chips .chip{min-width:48px;min-height:40px;cursor:pointer;border:1.5px solid var(--gold);background:var(--gold-soft);color:var(--retry-text);border-radius:10px;font:600 14px 'IBM Plex Mono',monospace;}
  .skip-btns{display:flex;flex-wrap:wrap;gap:10px;justify-content:center;margin-top:12px;}


  .kb-toggle{border:none;background:transparent;font-size:15px;cursor:pointer;padding:0 2px;vertical-align:middle;opacity:.7;}
  .vkb{position:fixed;left:0;right:0;bottom:0;z-index:80;background:var(--paper-2);border-top:1px solid var(--rule);box-shadow:0 -6px 20px rgba(0,0,0,.12);padding:6px 6px 8px;display:none;}
  .vkb.show{display:block;}
  .vkb-top{display:flex;justify-content:space-between;align-items:center;max-width:640px;margin:0 auto 4px;font:600 12px 'Source Sans 3',sans-serif;color:var(--ink-soft);}
  .vkb-link{border:none;background:none;color:var(--accent-text);font:600 12px 'Source Sans 3',sans-serif;cursor:pointer;text-decoration:underline;}
  .vkb-row{display:flex;gap:5px;max-width:640px;margin:0 auto 5px;}
  .vkb-k{flex:1;min-height:42px;border:1px solid var(--rule);border-radius:8px;background:var(--card);color:var(--ink);font:600 17px 'IBM Plex Mono',monospace;cursor:pointer;padding:0;}
  .vkb-k.fn{font:600 13px 'Source Sans 3',sans-serif;background:var(--gold-soft);}
  .vkb-k.done{background:var(--navy);color:#F4EFDF;border-color:var(--navy);}
  .vkb-k:active{transform:scale(.96);}
  body.kb-open .wrap{padding-bottom:360px;}
  body.kb-open .fab{display:none;}
  .tool-bar{display:flex;gap:8px;flex-wrap:wrap;margin:-4px 0 10px;}
  .tool-btn{min-height:36px;border:1.5px solid var(--gold);background:var(--gold-soft);color:var(--ink);border-radius:18px;padding:4px 12px;font:600 13.5px 'Source Sans 3',sans-serif;cursor:pointer;}
  .tool-panel{position:fixed;z-index:85;background:var(--card);border:1px solid var(--rule);border-radius:14px;box-shadow:0 10px 30px rgba(0,0,0,.25);display:none;}
  .tool-panel.show{display:block;}
  .tp-head{display:flex;align-items:center;gap:8px;padding:8px 10px;border-bottom:1px solid var(--rule);font:600 14px 'Source Sans 3',sans-serif;}
  .tp-note{font-size:12px;color:var(--ink-soft);font-weight:500;}
  .tp-x{margin-left:auto;border:1px solid var(--rule);background:var(--paper-2);color:var(--ink);border-radius:8px;min-height:32px;padding:2px 10px;cursor:pointer;font:600 13px 'Source Sans 3',sans-serif;}
  .tp-x + .tp-x{margin-left:0;}
  .calc{right:12px;bottom:84px;width:min(330px,calc(100vw - 24px));}
  body.calc-open .wrap{padding-bottom:440px;}
  body.calc-open .fab{display:none;}
  @media (max-width:640px){ .calc{left:6px;right:6px;width:auto;} .calc-keys button{min-height:36px;} }
  .calc-disp{padding:8px 12px;text-align:right;background:var(--paper-2);}
  .calc-expr{font:500 13px 'IBM Plex Mono',monospace;color:var(--ink-soft);min-height:18px;word-break:break-all;}
  .calc-res{font:600 24px 'IBM Plex Mono',monospace;color:var(--ink);word-break:break-all;}
  .calc-keys{display:grid;grid-template-columns:repeat(6,1fr);gap:5px;padding:8px;}
  .calc-keys button{min-height:40px;border:1px solid var(--rule);border-radius:8px;background:var(--card);color:var(--ink);font:600 14px 'IBM Plex Mono',monospace;cursor:pointer;padding:0;}
  .calc-keys button.fn{background:var(--gold-soft);font-family:'Source Sans 3',sans-serif;font-size:13px;}
  .calc-keys button.eq{grid-column:span 2;background:var(--navy);color:#F4EFDF;border-color:var(--navy);}
  .desmos{left:50%;top:50%;transform:translate(-50%,-50%);width:min(760px,calc(100vw - 16px));height:min(560px,calc(100vh - 90px));flex-direction:column;}
  .desmos.show{display:flex;}
  #desmosBox{flex:1;min-height:0;border-radius:0 0 14px 14px;overflow:hidden;}
  .desmos-msg{padding:24px;text-align:center;color:var(--ink-soft);}
  .chip[data-status="skipped"]{cursor:pointer;}
  .chip[data-status="answered"]{border-color:var(--accent-text);color:var(--accent-text);}


  button.crest-home{border:none;padding:0;position:relative;cursor:pointer;transition:transform .15s ease;}
  button.crest-home:hover,button.crest-home:focus-visible{transform:scale(1.06);outline:2px solid var(--gold);outline-offset:2px;}
  .crest-h{position:absolute;right:-7px;bottom:-7px;width:18px;height:18px;border-radius:50%;background:#F4EFDF;color:var(--navy);font:700 12px/18px 'Source Sans 3',sans-serif;text-align:center;box-shadow:0 1px 3px rgba(0,0,0,.3);}
  .brand .brand-row{position:relative;}
  .bmasw{position:absolute;left:50%;top:50%;transform:translate(-50%,-50%);display:flex;flex-shrink:0;white-space:nowrap;align-items:center;gap:6px;background:rgba(255,255,255,.12);border:1px solid rgba(255,255,255,.25);border-radius:99px;padding:5px 14px;color:#F4EFDF;}
  .bmasw-ic{font-size:16px;} .bmasw-t{font:600 20px 'IBM Plex Mono',monospace;letter-spacing:.02em;min-width:62px;text-align:center;}
  .bmasw-b{border:none;background:rgba(255,255,255,.18);color:#F4EFDF;border-radius:50%;width:30px;height:30px;cursor:pointer;font-size:13px;}
  .bmasw.off{display:none;}
  @media (max-width:560px){ .bmasw{position:static;transform:none;margin-left:auto;padding:4px 5px 4px 8px;gap:4px;} .bmasw-ic{display:none;} .bmasw-t{font-size:16px;min-width:48px;} .bmasw-b{width:26px;height:26px;} .brand .series-name{font-size:15px;} .brand .brand-name{font-size:10.5px;} .brand .brand-row>div:not(.bmasw){min-width:0;} }
  .bmasw-done{font:600 15px 'IBM Plex Mono',monospace;color:var(--accent-text);margin:4px 0 8px;}
  .sp-fab{position:fixed;left:14px;bottom:84px;z-index:60;border:1.5px solid var(--navy-2);background:var(--card);color:var(--ink);border-radius:99px;padding:9px 14px;font:700 14px 'Source Sans 3',sans-serif;box-shadow:0 4px 14px rgba(0,0,0,.15);cursor:pointer;}
  .sp-fab.on{background:var(--navy);color:#F4EFDF;}
  body.kb-open .sp-fab{display:none;}
  .sp-canvas{position:absolute;z-index:55;display:none;touch-action:none;cursor:crosshair;}
  .sp-canvas.passive{pointer-events:none;cursor:default;}
  .sp-bar{position:fixed;top:8px;left:8px;right:8px;margin:0 auto;width:max-content;z-index:90;display:none;align-items:center;gap:6px;background:var(--card);border:1px solid var(--rule);border-radius:14px;padding:6px 8px;box-shadow:0 6px 20px rgba(0,0,0,.2);max-width:calc(100vw - 16px);flex-wrap:wrap;justify-content:center;}
  .sp-lbl{font:700 13px 'Source Sans 3',sans-serif;color:var(--ink-soft);margin-right:2px;}
  .sp-pen,.sp-tool{width:38px;height:38px;border-radius:10px;border:1.5px solid var(--rule);background:var(--paper);cursor:pointer;display:inline-flex;align-items:center;justify-content:center;font-size:17px;padding:0;color:var(--ink);}
  .sp-pen i{width:20px;height:20px;border-radius:50%;display:block;}
  .sp-pen.on,.sp-tool.on{border-color:var(--navy-2);box-shadow:0 0 0 3px var(--gold-soft);}
  @media (max-width:560px){ .sp-lbl{display:none;} .sp-pen,.sp-tool{width:34px;height:34px;} .sp-fab span{display:none;} }

  /* larger reading sizes */
  .chapter-eyebrow{font-size:13.5px;}
  .chapter-title{font-size:36px;line-height:1.15;}
  .chapter-sub{font-size:16.5px;}
  .tab-btn{font-size:15.5px;}
  .sec-sub{font-size:15px;}
  .qtext{font-size:19px;line-height:1.55;}
  .qnum{width:36px;height:36px;font-size:16px;}
  .opt{font-size:17.5px;padding:12px 14px;}
  .step-line{font-size:17.5px;line-height:2;}
  .blank-input{font-size:16px;}
  .sol-line{font-size:16.5px;}
  .feedback{font-size:15px;}
  .note h2{font-size:28px;}
  .note h4{font-size:19px;}
  .note p,.note li{font-size:17.5px;line-height:1.65;}
  .note .lt{font-size:15.5px;}
  .ex .exh{font-size:18px;} .ex .exl{font-size:16.5px;}
  .keybox{font-size:16.5px;}
  .ttab{font-size:15.5px;}
  .hub-card h3{font-size:21px;} .hub-card p{font-size:15.5px;} .hub-btn{font-size:15px;}
  @media (max-width:480px){ .chapter-title{font-size:30px;} .qtext{font-size:18px;} .opt,.step-line{font-size:16.5px;} .note h2{font-size:24px;} .note p,.note li{font-size:16.5px;} }
</style>
</head>
<body>
<header class="brand">
  <div class="brand-row">
    <div class="crest">BM</div>
    <div>
      <div class="brand-name">Brain &amp; Mind Academy</div>
      <div class="series-name">Sopaan <span style="font-weight:400;font-size:14px;color:#CFD7EA;">Practice Series</span></div>
    </div>
  </div>
  <div class="chapter-eyebrow">Class 8 Mathematics · Chapter 3</div>
  <div class="chapter-title">Squares and Square Roots</div>
  <div class="chapter-sub">Theory Notes · Practice by Learning Objective · Learning Assessment</div><div class="chapter-credit">Mixed multiple-choice and fill-in-the-blank practice · Chapter 3</div>
  <div class="chapter-progress">
    <div class="cp-track"><div class="cp-fill" id="cpFill"></div></div>
    <div class="cp-label" id="cpLabel">0% complete</div>
  </div>
  <div class="who-row"><button class="mode-pill" id="modePill" hidden>Choose a mode</button><span class="who" id="whoBar" hidden></span></div>
</header>

<nav class="tabbar"><div class="tabbar-inner" id="tabbar"></div></nav>
<div class="sec-sub" id="secSub"></div><div class="slide-progress"><div class="sp-track"><div class="sp-fill" id="spFill"></div></div><div class="sp-label" id="spLabel">Question 1 of 49</div></div>
<div class="wrap" id="wrap"></div>
<footer class="brandfoot">Brain &amp; Mind Academy · Sopaan Practice Series · Class 8 Mathematics · Chapter 3<br>Chapter follows the Class 8 mathematics syllabus (New Enjoying Mathematics, Class 8). Theory notes, questions, learning assessments and worked solutions are written by Brain &amp; Mind Academy.</footer>

<div class="navbar"><div class="navbar-inner" id="navbarInner"></div></div>
<button class="fab" id="paletteFab"><span>Questions</span><span class="fab-badge" id="fabBadge">0/49</span></button>

<div class="overlay" id="overlay">
  <div class="palette" role="dialog" aria-label="Question palette">
    <div class="palette-head"><h2 id="paletteTitle">Question palette</h2><button class="palette-close" id="paletteClose">&times;</button></div>
    <div class="palette-legend">
      <span><i class="dot current"></i>Current</span><span><i class="dot correct"></i>Correct</span>
      <span><i class="dot revealed"></i>Revealed</span><span><i class="dot skipped"></i>Skipped</span>
      <span><i class="dot locked"></i>Locked</span>
    </div>
    <div class="chip-grid" id="paletteBody"></div>
  </div>
</div>
<div class="toast" id="toast"></div>

<script>
(function(){
"use strict";

/* ================= audio ================= */
var audioCtx=null;
function ensureAudio(){ if(!audioCtx){ try{ audioCtx=new (window.AudioContext||window.webkitAudioContext)(); }catch(e){} } return audioCtx; }
function playTone(freqs,dur,type){
  var ctx=ensureAudio(); if(!ctx) return;
  try{
    var t0=ctx.currentTime;
    freqs.forEach(function(f,i){
      var o=ctx.createOscillator(), g=ctx.createGain();
      o.type=type||'sine'; o.frequency.value=f;
      var start=t0+i*dur;
      g.gain.setValueAtTime(0.0001,start);
      g.gain.exponentialRampToValueAtTime(0.16,start+0.02);
      g.gain.exponentialRampToValueAtTime(0.0001,start+dur);
      o.connect(g); g.connect(ctx.destination);
      o.start(start); o.stop(start+dur+0.02);
    });
  }catch(e){}
}
function playSuccess(){ playTone([523.25,659.25,783.99],0.11,'sine'); }
function playWrong(){ playTone([220,185],0.14,'square'); }
function playReveal(){ playTone([300,220],0.16,'triangle'); }

/* ================= helpers ================= */
function norm(s){
  return String(s===undefined||s===null?'':s).trim().toLowerCase().replace(/\s+/g,'')
    .replace(/[×∗*·]/g,'x').replace(/÷/g,'/').replace(/–|—|−/g,'-')
    .replace(/[²]/g,'^2').replace(/[³]/g,'^3').replace(/[⁴]/g,'^4').replace(/[⁵]/g,'^5')
    .replace(/[⁶]/g,'^6').replace(/[⁷]/g,'^7').replace(/[⁸]/g,'^8').replace(/[⁹]/g,'^9')
    .replace(/\^/g,'');
}
function parseNum(s){
  if(s===undefined||s===null) return null;
  var t=String(s).trim().replace(/,/g,'').replace(/[−–—]/g,'-').replace(/\s+/g,''); if(t==='') return null;
  var neg=false; if(t[0]==='-'){neg=true;t=t.slice(1);}
  var m=t.match(/^(\d+)\/(\d+)$/);
  if(m){ var v=parseInt(m[1],10)/parseInt(m[2],10); return neg?-v:v; }
  if(/^\d+(\.\d+)?$/.test(t)){ var v2=parseFloat(t); return neg?-v2:v2; }
  return null;
}
/* ---- expression checker: compares answers like (P-2w)/2 and P/2-w at random values ---- */
function exprPrep(s){
  return String(s).toLowerCase().replace(/\s+/g,'').replace(/^[a-z]\(x\)=/i,'').replace(/^y=/i,'').replace(/[×∗·]/g,'*').replace(/÷/g,'/').replace(/[−–—]/g,'-')
    .replace(/²/g,'^2').replace(/³/g,'^3').replace(/⁴/g,'^4').replace(/⁵/g,'^5').replace(/⁶/g,'^6').replace(/⁷/g,'^7').replace(/⁸/g,'^8').replace(/⁹/g,'^9').replace(/π/g,'#').replace(/pi/gi,'#').replace(/½/g,'(1/2)');
}
function exprCompile(src){
  var s=exprPrep(src), i=0, toks=[], absDepth=0;
  while(i<s.length){
    var ch=s[i];
    if(/[0-9.]/.test(ch)){ var j=i; while(j<s.length && /[0-9.]/.test(s[j])) j++; toks.push({k:'n',v:parseFloat(s.slice(i,j))}); i=j; continue; }
    if(/[a-zA-Z#]/.test(ch)){ toks.push({k:'v',v:ch}); i++; continue; }
    if(ch==='|'){ var pv=toks[toks.length-1]; var opn=(absDepth===0)||!pv||('+-*/^(['.indexOf(pv.k)>=0); if(opn){ absDepth++; toks.push({k:'['}); } else { absDepth--; toks.push({k:']'}); } i++; continue; }
    if('+-*/^()'.indexOf(ch)>=0){ toks.push({k:ch}); i++; continue; }
    return null;
  }
  var out=[];
  for(var t=0;t<toks.length;t++){
    var a=toks[t], b=out[out.length-1];
    if(b && (b.k==='n'||b.k==='v'||b.k===')'||b.k===']') && (a.k==='n'||a.k==='v'||a.k==='('||a.k==='[')) out.push({k:'&'});
    out.push(a);
  }
  var p=0;
  function peek(){ return out[p]; }
  function parseE(){ var n=parseT(); while(peek() && (peek().k==='+'||peek().k==='-')){ var o=out[p++].k, r=parseT(); n=(function(l,r,o){return function(e){ return o==='+'?l(e)+r(e):l(e)-r(e); };})(n,r,o); } return n; }
  function parseI(){ var n=parseU(); while(peek() && peek().k==='&'){ p++; var r=parseP(); n=(function(l,r){return function(e){ return l(e)*r(e); };})(n,r); } return n; }
  function parseT(){ var n=parseI(); while(peek() && (peek().k==='*'||peek().k==='/')){ var o=out[p++].k, r=parseI(); n=(function(l,r,o){return function(e){ return o==='*'?l(e)*r(e):l(e)/r(e); };})(n,r,o); } return n; }
  function parseU(){ if(peek() && peek().k==='-'){ p++; var u=parseU(); return function(e){ return -u(e); }; } if(peek() && peek().k==='+'){ p++; return parseU(); } return parseP(); }
  function parseP(){ var b=parseA(); if(peek() && peek().k==='^'){ p++; var x=parseU(); return function(e){ return Math.pow(b(e),x(e)); }; } return b; }
  function parseA(){
    var t=out[p++]; if(!t) throw 0;
    if(t.k==='n') return function(){ return t.v; };
    if(t.k==='v') return t.v==='#' ? function(){ return Math.PI; } : function(e){ return e[t.v]; };
    if(t.k==='('){ var n=parseE(); if(!peek()||peek().k!==')') throw 0; p++; return n; }
    if(t.k==='['){ var m=parseE(); if(!peek()||peek().k!==']') throw 0; p++; return function(e){ return Math.abs(m(e)); }; }
    throw 0;
  }
  try{ var f=parseE(); if(p!==out.length) return null; return f; }catch(e){ return null; }
}
function exprEqual(input,answer){
  var f=exprCompile(input), g=exprCompile(answer); if(!f||!g) return false;
  var hits=0;
  for(var trial=0;trial<8;trial++){
    var env={}; 'abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ'.split('').forEach(function(c){ env[c]=1.3+Math.random()*4.1; });
    var x=f(env), y=g(env);
    if(!isFinite(x)||!isFinite(y)) continue;
    if(Math.abs(x-y)>1e-7*Math.max(1,Math.abs(x),Math.abs(y))) return false;
    hits++;
  }
  return hits>=3;
}
function wordsNorm(s){ return String(s||'').toLowerCase().replace(/\band\b/g,' ').replace(/[^a-z]/g,''); }
function listNorm(s){ return (String(s||'').replace(/[−–—]/g,'-').replace(/(\d) (?=\d{3}\b)/g,'$1').match(/-?\d+(\.\d+)?/g)||[]).join(','); }
function powNorm(s){ return String(s||'').toLowerCase().replace(/\s+/g,'').replace(/[×∗*·.]/g,'x').replace(/[⁰¹²³⁴⁵⁶⁷⁸⁹]+/g,function(m){ return '^'+m.split('').map(function(c){ return '⁰¹²³⁴⁵⁶⁷⁸⁹'.indexOf(c); }).join(''); }).replace(/\^1(?!\d)/g,''); }
function fr(s){ return String(s).replace(/\{(\d+) (\d+)\/(\d+)\}/g,'<span class="mx">$1<span class="fq"><span>$2</span><span>$3</span></span></span>').replace(/\{(\d+)\/(\d+)\}/g,'<span class="fq"><span>$1</span><span>$2</span></span>'); }
function gcdI(a,b){ a=Math.abs(a); b=Math.abs(b); while(b){ var t=a%b; a=b; b=t; } return a; }
function fracParse(s){ s=String(s===undefined||s===null?'':s).trim().replace(/[\u2044\u2215\u00f7]/g,'/').replace(/\s+/g,' ').replace(/\s*\/\s*/g,'/'); var m;
  if((m=s.match(/^(-?\d+)$/))) return {v:+m[1],form:'int',n:+m[1],d:1};
  if((m=s.match(/^(-?\d+)\/(\d+)$/))){ if(+m[2]===0) return null; return {v:m[1]/m[2],form:'frac',n:+m[1],d:+m[2]}; }
  if((m=s.match(/^(-?)(\d+)(?: |\+)(\d+)\/(\d+)$/))){ if(+m[4]===0) return null; var sg=m[1]?-1:1; return {v:sg*(+m[2]+m[3]/m[4]),form:'mixed',w:sg*m[2],n:+m[3],d:+m[4]}; }
  if((m=s.match(/^-?\d*\.\d+$/))) return {v:parseFloat(s),form:'dec'};
  return null; }
function fracOK(mode,input,answer){
  if(mode==='flist'){ var A=String(input).split(/[,;]/).map(function(x){return x.trim();}).filter(Boolean), K=String(answer).split(/[,;]/).map(function(x){return x.trim();});
    if(A.length!==K.length) return false; return A.every(function(x,i){ var a=fracParse(x), k=fracParse(K[i]); return a&&k&&Math.abs(a.v-k.v)<1e-9; }); }
  var a=fracParse(input), k=fracParse(answer); if(!a||!k) return false;
  var same=Math.abs(a.v-k.v)<1e-9; if(!same) return false;
  if(mode==='fv') return true;
  if(mode==='dec') return a.form==='dec'||a.form==='int';
  if(mode==='fe') return (a.form==='frac'&&k.form==='frac'&&a.n===k.n&&a.d===k.d)||(a.form==='int'&&k.form==='int');
  if(mode==='fi') return a.form==='frac'||(a.form==='int'&&k.form==='int');
  if(mode==='fl') return a.form==='int'||(a.form==='frac'&&gcdI(a.n,a.d)===1)||(a.form==='mixed'&&a.n<a.d&&gcdI(a.n,a.d)===1);
  if(mode==='fm') return a.form==='int'||(a.form==='mixed'&&a.n>0&&a.n<a.d&&gcdI(a.n,a.d)===1);
  return false; }
function answerMatches(input,answer,accept,expr){
  if(expr==='dec'||expr==='fv'||expr==='fe'||expr==='fl'||expr==='fm'||expr==='fi'||expr==='flist'){ if(input===undefined||input===null||String(input).trim()==='') return false; return fracOK(expr,input,answer); }
  if(input===undefined||input===null||String(input).trim()==='') return false;
  if(expr==='words'){ return [answer].concat(accept||[]).some(function(a){ if(/\d/.test(a)) return norm(a)===norm(input); var w=wordsNorm(a); return w!=='' && w===wordsNorm(input); }); }
  if(expr==='list'){ return [answer].concat(accept||[]).some(function(a){ return listNorm(a)===listNorm(input); }); }
  if(expr==='pow'){ return [answer].concat(accept||[]).some(function(a){ return powNorm(a)===powNorm(input); }); }
  if(expr==='time'){ var tn=function(x){ var t=String(x).toLowerCase().replace(/[\s.]/g,'').replace(/[:h]/g,''); if(/^\d{3}(am|pm)?$/.test(t)) t='0'+t; return t; }; return [answer].concat(accept||[]).some(function(a){ return tn(a)===tn(input); }); }
  if(expr==='glist'){ var gn=function(x){ return String(x).toUpperCase().split(/[\s,;]+/).filter(Boolean).sort().join(','); }; return [answer].concat(accept||[]).some(function(a){ return gn(a)===gn(input); }); }
  if(expr==='coord'){ var cn=function(x){ return String(x).replace(/[\u2212\u2013\u2014]/g,'-').replace(/[\s()\[\]]/g,''); }; return [answer].concat(accept||[]).some(function(a){ return cn(a)===cn(input); }); }
  if(expr==='dlist'){ var dn=function(x){ return (String(x).replace(/[−–—]/g,'-').match(/-?\d*\.?\d+/g)||[]).map(Number).join(','); }; return [answer].concat(accept||[]).some(function(a){ return dn(a)===dn(input); }); }
  if(expr==='set'){ var sn=function(x){ return (String(x).match(/-?\d+/g)||[]).map(Number).sort(function(a,b){return a-b;}).join(','); }; return [answer].concat(accept||[]).some(function(a){ return sn(a)===sn(input); }); }
  if(expr==='primes'){ var pn=function(x){ var t=powNorm(x).replace(/[^0-9x^]/g,''); var out=[]; t.split('x').forEach(function(tok){ if(!tok) return; var m=tok.split('^'); var b=+m[0], e=m[1]?+m[1]:1; for(var i=0;i<e;i++) out.push(b); }); return out.sort(function(a,b){return a-b;}).join(','); }; return [answer].concat(accept||[]).some(function(a){ return pn(a)===pn(input); }); }
  if(expr==='angle'){ var an=function(x){ return String(x).toUpperCase().replace(/[^A-Z]/g,''); }; var k=an(answer), v=an(input); return v===k || v===k.split('').reverse().join(''); }
  if(expr==='trans'){ var tv=function(x){ var s=String(x).toLowerCase().replace(/[−–—]/g,'-').replace(/\b(units?|squares?|and|then|steps?|to|the|a)\b/g,' ').replace(/[,;.]/g,' '); var re=/(\d+)\s*(right|left|up|down|r|l|u|d)\b/g, m, dx=0, dy=0, n=0; while((m=re.exec(s))){ var v=+m[1], d=m[2][0]; if(d==='r')dx+=v; else if(d==='l')dx-=v; else if(d==='u')dy+=v; else dy-=v; n++; } if(!n||s.replace(re,'').replace(/\s+/g,'')!=='') return null; return dx+','+dy; }; var ti=tv(input); return ti!==null && [answer].concat(accept||[]).some(function(a){ return tv(a)===ti; }); }
  if(expr==='rot'){ var rv=function(x){ var s=String(x).toLowerCase().replace(/quarter[\s-]*turn/g,'90').replace(/half[\s-]*turn/g,'180').replace(/three[\s-]*quarter[\s-]*turn/g,'270'); var m=s.match(/\b(90|180|270)\b/); if(!m) return null; var a=+m[1]; if(a===180) return '180'; var dir=/anti|counter|acw|ccw/.test(s)?-1:(/clockwise|\bcw\b/.test(s)?1:0); if(!dir) return null; return String(((a*dir)%360+360)%360); }; var ri=rv(input); return ri!==null && ri===rv(answer); }
  if(expr==='expanded'){ var f=function(x){ return String(x).replace(/\s+/g,'').replace(/,/g,''); }; return [answer].concat(accept||[]).some(function(a){ return f(a)===f(input); }); }
  if(expr===true && input!==undefined && input!==null && String(input).trim()!==''){
    if(exprEqual(input,answer)) return true;
    var alt=String(input).replace(/\/\s*(\d+(?:\.\d+)?)\s*([a-zA-Z(])/g,'/$1*$2'); if(alt!==String(input) && exprEqual(alt,answer)) return true;
    return (accept||[]).some(function(a){ return exprEqual(input,a); });
  }
  if(input===undefined||input===null||String(input).trim()==='') return false;
  var n1=parseNum(input), n2=parseNum(answer);
  if(n1!==null && n2!==null){ if(Math.abs(n1-n2)<1e-3) return true; return (accept||[]).some(function(a){ var n3=parseNum(a); return n3!==null && Math.abs(n1-n3)<1e-3; }); }
  var cands=[answer].concat(accept||[]); var ni=norm(input);
  for(var i=0;i<cands.length;i++){ if(norm(cands[i])===ni) return true; }
  return false;
}
function esc(s){ return String(s).replace(/&/g,'&amp;').replace(/</g,'&lt;'); }

/* ================= DATA ================= */
var AR_OPTIONS = ["Both A and R are true, and R is the correct explanation of A","Both A and R are true, but R is NOT the correct explanation of A","A is true but R is false","A is false but R is true"];
var THEORY = "<div class=\"hub\"><div class=\"hub-card\"><h3>📖 Theory notes</h3><p>Explained notes for every part of the chapter: properties of squares, patterns, and three ways to find square roots, with the book’s worked examples.</p><div class=\"hub-btns\"><button class=\"hub-btn\" data-jump=\"n31\">3.1 notes</button><button class=\"hub-btn\" data-jump=\"n32\">3.2 notes</button><button class=\"hub-btn\" data-jump=\"n33\">3.3 notes</button><button class=\"hub-btn\" data-jump=\"n34\">3.4 notes</button><button class=\"hub-btn\" data-jump=\"n35\">3.5 notes</button><button class=\"hub-btn\" data-jump=\"n36\">3.6 notes</button></div></div><div class=\"hub-card\"><h3>🎯 Practice by learning objective</h3><p>Every Example, Try This and Exercise question from the chapter, sorted by objective, mixing multiple-choice and fill-in-the-blank questions.</p><div class=\"hub-btns\"><button class=\"hub-btn\" data-go=\"s1\">3.1 · Squares of numbers</button><button class=\"hub-btn\" data-go=\"s2\">3.2 · Properties of square numbers</button><button class=\"hub-btn\" data-go=\"s3\">3.3 · Pythagorean triplets and patterns</button><button class=\"hub-btn\" data-go=\"s4\">3.4 · Square roots by prime factorisation</button><button class=\"hub-btn\" data-go=\"s5\">3.5 · Division method, fractions and decimals</button><button class=\"hub-btn\" data-go=\"s6\">3.6 · Estimation and applications</button></div></div><div class=\"hub-card\"><h3>📝 Learning assessment</h3><p>Four short assessments built from the Chapter Check-up. Take them in Quiz mode and open the report to see your results as pie charts.</p><div class=\"hub-btns\"><button class=\"hub-btn\" data-go=\"s7\">A · Knowing and understanding</button><button class=\"hub-btn\" data-go=\"s8\">B · Investigating patterns</button><button class=\"hub-btn\" data-go=\"s9\">C · Communicating</button><button class=\"hub-btn\" data-go=\"s10\">D · Applying mathematics in real-life contexts</button><button class=\"hub-btn primary\" data-go=\"report\">📊 View my report</button></div></div></div><section class=\"note\" id=\"nintro\"><h2>About this chapter</h2><p>When a number is multiplied by itself, it is <b>squared</b>: 5<sup>2</sup> = 5 × 5 = 25. Going backwards, 5 is the <b>square root</b> of 25, written √25 = 5. This chapter looks at the patterns hidden in square numbers and at three ways of finding square roots.</p><div class=\"tscroll\"><table class=\"ttab\"><tr><th>Assessment</th><th>Skill area</th><th>What it checks</th></tr><tr><td>A</td><td>Knowing and understanding</td><td>Squares, square roots and perfect squares.</td></tr><tr><td>B</td><td>Investigating patterns</td><td>Nearest perfect squares, estimating roots and patterns in squares.</td></tr><tr><td>C</td><td>Communicating</td><td>The division method, decimal roots and explaining the properties.</td></tr><tr><td>D</td><td>Applying mathematics in real-life contexts</td><td>Areas, sides and distances using square roots and Pythagoras’ theorem.</td></tr></table></div><p><b>Tools:</b> ⏱ at the top shows the time since you signed in. ✏️ opens a scratchpad with four pens for rough work. Tap the BM badge to go back to the home page.</p><p><b>Typing answers:</b> a square root means the <b>positive</b> square root, so type 12, not −12. Type fractions as <span class=\"mono\">3/8</span> in lowest terms and decimals as <span class=\"mono\">2.6</span>. Where a word is asked for (odd / even), type the word.</p></section><section class=\"note\" id=\"n31\"><h2>3.1 Squares of numbers</h2><p class=\"lt\"><b>Objective:</b> Find the squares of whole numbers, integers, fractions and decimals, and recognise perfect squares.</p><p>The <b>square</b> of a number x is x × x, written x<sup>2</sup> and read “x squared”. For example 7<sup>2</sup> = 7 × 7 = 49, so 49 is the square of 7.</p><div class=\"tscroll\"><table class=\"ttab\"><tr><th>n</th><th>n<sup>2</sup></th><th>n</th><th>n<sup>2</sup></th><th>n</th><th>n<sup>2</sup></th><th>n</th><th>n<sup>2</sup></th></tr><tr><td>1</td><td>1</td><td>6</td><td>36</td><td>11</td><td>121</td><td>16</td><td>256</td></tr><tr><td>2</td><td>4</td><td>7</td><td>49</td><td>12</td><td>144</td><td>17</td><td>289</td></tr><tr><td>3</td><td>9</td><td>8</td><td>64</td><td>13</td><td>169</td><td>18</td><td>324</td></tr><tr><td>4</td><td>16</td><td>9</td><td>81</td><td>14</td><td>196</td><td>19</td><td>361</td></tr><tr><td>5</td><td>25</td><td>10</td><td>100</td><td>15</td><td>225</td><td>20</td><td>400</td></tr></table></div><h4>Square of a rational number</h4><p>Square the numerator and the denominator separately: ({a/b})<sup>2</sup> = a<sup>2</sup>/b<sup>2</sup>. A decimal is squared like a whole number, then the answer gets twice as many decimal places: 0.3<sup>2</sup> = 0.09.</p><div class=\"ex\"><div class=\"exh\">Worked example (Example 2)</div><div class=\"exl\">({−3/2})<sup>2</sup> = ({−3/2}) × ({−3/2}) = ((−3) × (−3))/(2 × 2) = <b>{9/4}</b>.<br>({5/8})<sup>2</sup> = (5 × 5)/(8 × 8) = <b>{25/64}</b>.</div></div><p>The square of any rational number, positive or negative, is <b>never negative</b>: (−3)<sup>2</sup> = 9 = 3<sup>2</sup>, and in general x<sup>2</sup> = (−x)<sup>2</sup>.</p><h4>Perfect squares</h4><p>A number is a <b>perfect square</b> (square number) if it is the square of a whole number: 1, 4, 9, 16, 25, … Numbers such as 5, 6, 8, 13 and 14 are not perfect squares.</p><div class=\"keybox\"><b>Common mistake:</b> −3<sup>2</sup> = −(3 × 3) = −9, but (−3)<sup>2</sup> = (−3) × (−3) = 9. The bracket decides what is squared.</div><div class=\"hub-btns\" style=\"margin-top:12px\"><button class=\"hub-btn primary\" data-go=\"s1\">Practise 3.1 →</button></div></section><section class=\"note\" id=\"n32\"><h2>3.2 Properties of square numbers</h2><p class=\"lt\"><b>Objective:</b> Use units digits, zeros, odd/even and digit-count properties and the sum of consecutive odd numbers to reason about squares.</p><div class=\"tscroll\"><table class=\"ttab\"><tr><th>Property</th><th>What it says</th><th>Example</th></tr><tr><td>1 · units digit</td><td>A square ends in 0, 1, 4, 5, 6 or 9 — never in 2, 3, 7 or 8.</td><td>4867 is not a square.</td></tr><tr><td>2 · units digit of the square</td><td>Units digit 1 or 9 → square ends in 1; 2 or 8 → 4; 3 or 7 → 9; 4 or 6 → 6; 5 → 5; 0 → 0.</td><td>68<sup>2</sup> ends in 4 (8 × 8 = 64).</td></tr><tr><td>3 · zeros</td><td>A number ending in an <b>odd</b> number of zeros is never a perfect square.</td><td>81,000 = 9<sup>2</sup> × 10<sup>2</sup> × 10</td></tr><tr><td>4 · odd / even</td><td>Squares of even numbers are even; squares of odd numbers are odd.</td><td>6<sup>2</sup> = 36, 7<sup>2</sup> = 49</td></tr><tr><td>5 · number of digits</td><td>The square of an n-digit number has 2n − 1 or 2n digits.</td><td>12<sup>2</sup> = 144 (3), 41<sup>2</sup> = 1681 (4)</td></tr><tr><td>6 · odd numbers</td><td>1 + 3 + 5 + … (n odd numbers) = n<sup>2</sup>.</td><td>1 + 3 + 5 + 7 = 16 = 4<sup>2</sup></td></tr><tr><td>7 · numbers between</td><td>There are 2n numbers between n<sup>2</sup> and (n + 1)<sup>2</sup>.</td><td>Between 9 and 16: 6 numbers</td></tr></table></div><p>Property 1 only tells us which numbers are <b>certainly not</b> squares. A number ending in 1, 4, 5, 6, 9 or 0 may or may not be a square: 35 ends in 5 but is not a square.</p><div class=\"ex\"><div class=\"exh\">Worked example (Example 4)</div><div class=\"exl\">Which of 3486, 4867, 8913 cannot be perfect squares?<br>4867 ends in 7 and 8913 ends in 3, so they are <b>certainly not</b> perfect squares. 3486 ends in 6, so it might be one (4 × 4 and 6 × 6 end in 6).</div></div><div class=\"ex\"><div class=\"exh\">Worked example (Example 5)</div><div class=\"exl\">Units digit of 24<sup>2</sup>: 4 × 4 = 16 → <b>6</b>. Of 68<sup>2</sup>: 8 × 8 = 64 → <b>4</b>. Of 45<sup>2</sup>: 5 × 5 = 25 → <b>5</b>.</div></div><div class=\"keybox\"><b>Sum of odd numbers:</b> 15<sup>2</sup> is the sum of the first 15 odd numbers, 1 + 3 + 5 + … + 29. The last odd number is 2n − 1.</div><div class=\"hub-btns\" style=\"margin-top:12px\"><button class=\"hub-btn primary\" data-go=\"s2\">Practise 3.2 →</button></div></section><section class=\"note\" id=\"n33\"><h2>3.3 Pythagorean triplets and patterns</h2><p class=\"lt\"><b>Objective:</b> Identify Pythagorean triplets, use triangular numbers and square patterns, and square numbers ending in 5 quickly.</p><h4>Pythagorean triplets (Property 8)</h4><p>Three natural numbers a, b, c form a <b>Pythagorean triplet</b> if a<sup>2</sup> + b<sup>2</sup> = c<sup>2</sup>, e.g. 3, 4, 5 (9 + 16 = 25); 5, 12, 13; 9, 12, 15. For any integer m > 1, <b>2m, m<sup>2</sup> − 1 and m<sup>2</sup> + 1</b> form a triplet: m = 7 gives 14, 48, 50 (196 + 2304 = 2500).</p><p>By <b>Pythagoras’ theorem</b>, in a right-angled triangle the square of the hypotenuse equals the sum of the squares of the other two sides.</p><h4>Triangular numbers (Property 9)</h4><p>1, 3, 6, 10, 15, 21, … are sums of consecutive numbers (1, 1 + 2, 1 + 2 + 3, …). The nth triangular number is <b>n(n + 1)/2</b>. Adding two consecutive triangular numbers gives the square of the higher term number: 10 + 15 = 25 = 5<sup>2</sup>.</p><h4>Other square patterns</h4><ul><li>Property 10: n<sup>2</sup> = 2(n − 1)<sup>2</sup> − (n − 2)<sup>2</sup> + 2.</li><li>Property 11: n<sup>2</sup> = 2(1 + 2 + … + (n − 1)) + n.</li><li>Property 12: n<sup>2</sup> = (n − 1)(n + 1) + 1.</li></ul><div class=\"ex\"><div class=\"exh\">Worked examples (Examples 6–8)</div><div class=\"exl\">10<sup>2</sup> = 2(9)<sup>2</sup> − 8<sup>2</sup> + 2 = 162 − 64 + 2 = <b>100</b>.<br>10<sup>2</sup> = 2(1 + 2 + … + 9) + 10 = 2 × 45 + 10 = <b>100</b>.<br>31<sup>2</sup> = 30 × 32 + 1 = 960 + 1 = <b>961</b>.</div></div><h4>Squaring a number ending in 5</h4><p>Write 25 at the end; in front of it write (tens digit) × (tens digit + 1).</p><div class=\"ex\"><div class=\"exh\">Worked example</div><div class=\"exl\">35<sup>2</sup>: 3 × 4 = 12, so 35<sup>2</sup> = <b>1225</b>.<br>75<sup>2</sup>: 7 × 8 = 56, so 75<sup>2</sup> = <b>5625</b>.</div></div><div class=\"keybox\"><b>Did you know?</b> A square leaves remainder 0 or 1 when divided by 3 or by 4, and the square of an odd number is the sum of two consecutive numbers: 7<sup>2</sup> = 24 + 25.</div><div class=\"hub-btns\" style=\"margin-top:12px\"><button class=\"hub-btn primary\" data-go=\"s3\">Practise 3.3 →</button></div></section><section class=\"note\" id=\"n34\"><h2>3.4 Square roots by prime factorisation</h2><p class=\"lt\"><b>Objective:</b> Find square roots of perfect squares and simple algebraic terms by pairing prime factors.</p><p>The <b>square root</b> of y is the number x with x × x = y, written x = √y. Since 7<sup>2</sup> = 49, √49 = 7. Every square number has two square roots (5 × 5 = 25 and (−5) × (−5) = 25), but in this chapter <b>√ means the positive root</b>.</p><h4>Prime factorisation method</h4><ol><li>Write the number as a product of prime factors.</li><li>Make pairs of equal factors.</li><li>Take one factor from every pair and multiply.</li></ol><div class=\"ex\"><div class=\"exh\">Worked example (Example 10)</div><div class=\"exl\">144 = (2 × 2) × (2 × 2) × (3 × 3), so √144 = 2 × 2 × 3 = <b>12</b>.</div></div><div class=\"ex\"><div class=\"exh\">Worked example (Example 15)</div><div class=\"exl\">1764 = (2 × 2) × (3 × 3) × (7 × 7), so √1764 = 2 × 3 × 7 = <b>42</b>.</div></div><div class=\"ex\"><div class=\"exh\">Worked example (Example 16)</div><div class=\"exl\">√(9a<sup>4</sup>b<sup>8</sup>) = √(3 × 3 × a<sup>2</sup> × a<sup>2</sup> × b<sup>4</sup> × b<sup>4</sup>) = <b>3a<sup>2</sup>b<sup>4</sup></b> (halve each exponent).</div></div><h4>Number of digits in a square root</h4><p>Put a bar over every pair of digits starting from the units digit (a single leftover digit on the left also gets a bar). The number of bars is the number of digits in the square root: 4|56|86 has 3 bars, so its root has 3 digits.</p><h4>Repeated subtraction</h4><p>Subtract 1, 3, 5, 7, … in turn. For a perfect square you reach 0; the number of subtractions is the root. 49 − 1 − 3 − 5 − 7 − 9 − 11 − 13 = 0 after 7 steps, so √49 = 7.</p><div class=\"keybox\"><b>Check:</b> if a prime factor is left without a partner, the number is not a perfect square.</div><div class=\"hub-btns\" style=\"margin-top:12px\"><button class=\"hub-btn primary\" data-go=\"s4\">Practise 3.4 →</button></div></section><section class=\"note\" id=\"n35\"><h2>3.5 Division method, fractions and decimals</h2><p class=\"lt\"><b>Objective:</b> Find square roots by the long division method, including rational numbers, decimals and approximate roots.</p><p>For large numbers the <b>long division method</b> is quicker than factorising.</p><ol><li>Mark pairs of digits (periods) from the units digit.</li><li>Find the largest square ≤ the first period; write its root as the first digit of the answer and as the first divisor. Subtract.</li><li>Bring down the next period. Double the answer so far to start the new divisor, then find the digit a so that (new divisor with a on the end) × a is as large as possible without going over.</li><li>Repeat until all periods are used.</li></ol><div class=\"ex\"><div class=\"exh\">Worked example (Example 18) · √2916</div><div class=\"exl\">Periods 29 | 16. 5<sup>2</sup> = 25 ≤ 29, remainder 4. Bring down 16 → 416.<br>Double 5 → 10_: 104 × 4 = 416, remainder 0. So √2916 = <b>54</b>.</div></div><div class=\"tscroll\"><table class=\"ttab\"><tr><th>Divisor</th><th>Dividend</th><th>Subtract</th><th>Remainder</th></tr><tr><td>5</td><td>27</td><td>5 × 5 = 25</td><td>2</td></tr><tr><td>102</td><td>245</td><td>102 × 2 = 204</td><td>41</td></tr><tr><td>1044</td><td>4176</td><td>1044 × 4 = 4176</td><td>0</td></tr></table></div><p style=\"text-align:center\">Example 19: √274576 = <b>524</b></p><h4>Rational numbers</h4><p>√({a/b}) = √a / √b. Change a mixed number to an improper fraction first: 17{137/256} = {4489/256}, so the root is {67/16} = 4{3/16}.</p><h4>Decimals</h4><p>Pair the whole-number part from right to left and the decimal part from <b>left to right</b> (add a zero if needed: 6734.834 → 67 34 . 83 40). Put the decimal point in the root when the first decimal pair is brought down.</p><div class=\"tscroll\"><table class=\"ttab\"><tr><th>Divisor</th><th>Dividend</th><th>Subtract</th><th>Remainder</th></tr><tr><td>5</td><td>31</td><td>5 × 5 = 25</td><td>6</td></tr><tr><td>106</td><td>680</td><td>106 × 6 = 636</td><td>44</td></tr><tr><td>1124</td><td>4496</td><td>1124 × 4 = 4496</td><td>0</td></tr></table></div><p style=\"text-align:center\">Example 23: √3180.96 = <b>56.4</b></p><h4>Numbers that are not perfect squares</h4><p>Add pairs of zeros after the point, work to 3 decimal places and round to 2: √7896 = 88.859… ≈ <b>88.86</b>.</p><div class=\"keybox\"><b>Remember:</b> a remainder of 0 at the end means the number is a perfect square.</div><div class=\"hub-btns\" style=\"margin-top:12px\"><button class=\"hub-btn primary\" data-go=\"s5\">Practise 3.5 →</button></div></section><section class=\"note\" id=\"n36\"><h2>3.6 Estimation and applications</h2><p class=\"lt\"><b>Objective:</b> Estimate square roots and solve problems on perfect squares, areas, sides and hypotenuses.</p><h4>Estimating a square root</h4><p>251 lies between 100 = 10<sup>2</sup> and 400 = 20<sup>2</sup>; closer in, 15<sup>2</sup> = 225 and 16<sup>2</sup> = 256. 251 is nearer 256, so √251 ≈ 16.</p><h4>Root of a 3- or 4-digit perfect square</h4><ol><li>Units digit of the square → two choices for the units digit of the root (6 → 4 or 6; 4 → 2 or 8; 9 → 3 or 7; 1 → 1 or 9).</li><li>Ignore the last two digits; the largest square ≤ what is left gives the tens digit.</li><li>Compare with the square of the number ending in 5 in between.</li></ol><div class=\"ex\"><div class=\"exh\">Worked example (Example 32) · √3136</div><div class=\"exl\">Units digit 6 → root ends in 4 or 6. 5<sup>2</sup> = 25 ≤ 31 < 36, so the root is 54 or 56.<br>55<sup>2</sup> = 3025 < 3136, so √3136 = <b>56</b>.</div></div><h4>Nearest perfect square</h4><p>Divide by the long division method. The remainder shows how far the number is above a perfect square.</p><div class=\"ex\"><div class=\"exh\">Worked example (Example 25)</div><div class=\"exl\">√9999: the division leaves remainder 198, so 9999 − 198 = <b>9801</b> (= 99<sup>2</sup>) is the greatest 4-digit perfect square.</div></div><div class=\"ex\"><div class=\"exh\">Worked example (Example 26)</div><div class=\"exl\">79380 = 2<sup>2</sup> × 3<sup>4</sup> × 7<sup>2</sup> × 5. The 5 has no partner, so multiply or divide by <b>5</b> to get a perfect square.</div></div><div class=\"ex\"><div class=\"exh\">Worked example (Example 30)</div><div class=\"exl\">A hall is 24 m by 18 m. Longest straight line = diagonal: 24<sup>2</sup> + 18<sup>2</sup> = 576 + 324 = 900, and √900 = <b>30 m</b>.</div></div><div class=\"keybox\"><b>Area and side:</b> area of a square = side<sup>2</sup>, so side = √area; perimeter = 4 × side.</div><div class=\"hub-btns\" style=\"margin-top:12px\"><button class=\"hub-btn primary\" data-go=\"s6\">Practise 3.6 →</button></div></section><section class=\"note\" id=\"nsum\"><h2>Chapter checklist</h2><ul><li>Find the squares of whole numbers, integers, fractions and decimals, and recognise perfect squares.</li><li>Use units digits, zeros, odd/even and digit-count properties and the sum of consecutive odd numbers to reason about squares.</li><li>Identify Pythagorean triplets, use triangular numbers and square patterns, and square numbers ending in 5 quickly.</li><li>Find square roots of perfect squares and simple algebraic terms by pairing prime factors.</li><li>Find square roots by the long division method, including rational numbers, decimals and approximate roots.</li><li>Estimate square roots and solve problems on perfect squares, areas, sides and hypotenuses.</li></ul><div class=\"hub-btns\" style=\"margin-top:10px\"><button class=\"hub-btn\" data-go=\"s7\">Assessment A</button><button class=\"hub-btn\" data-go=\"s8\">Assessment B</button><button class=\"hub-btn\" data-go=\"s9\">Assessment C</button><button class=\"hub-btn\" data-go=\"s10\">Assessment D</button><button class=\"hub-btn primary\" data-go=\"report\">📊 Report</button></div></section>";
var REPORT = [["s7", "A", "Knowing and understanding"], ["s8", "B", "Investigating patterns"], ["s9", "C", "Communicating"], ["s10", "D", "Applying mathematics in real-life contexts"]];
var SECTIONS = [{"id": "s1", "label": "3.1 Squares", "sub": "Squares of whole numbers, integers, fractions and decimals; perfect squares", "slides": [{"kind": "blank", "p": "<b>Looking Back · Q1</b> · Factorise into prime factors (type the exponents).", "tag": "", "marks": "", "flat": [{"t": "a) 81 = 3 to the power __B1__", "a": {"B1": "4"}}, {"t": "b) 100 = 2<sup>m</sup> × 5<sup>n</sup>:  m = __B1__ ,  n = __B2__", "a": {"B1": "2", "B2": "2"}}, {"t": "c) 196 = 2<sup>m</sup> × 7<sup>n</sup>:  m = __B1__ ,  n = __B2__", "a": {"B1": "2", "B2": "2"}}], "sol": "81 = 3 × 3 × 3 × 3 = 3<sup>4</sup>.\n100 = 2 × 2 × 5 × 5 = 2<sup>2</sup> × 5<sup>2</sup>.\n196 = 2 × 2 × 7 × 7 = 2<sup>2</sup> × 7<sup>2</sup>."}, {"kind": "mcq", "text": "<b>Looking Back · Q2</b> · If x is any number, then “x squared” is written as", "opts": ["√x", "x + x", "x<sup>2</sup>", "2x"], "correct": 2, "tag": "", "sol": "x squared means x × x, written x<sup>2</sup>. (2x = x + x is x doubled; √x is the square root.)"}, {"kind": "blank", "p": "<b>Looking Back · Q3</b> · Write in power notation using prime factorisation (type the exponents).", "tag": "", "marks": "", "flat": [{"t": "a) 4 = 2 to the power __B1__", "a": {"B1": "2"}}, {"t": "b) 25 = 5 to the power __B1__", "a": {"B1": "2"}}, {"t": "c) 121 = 11 to the power __B1__", "a": {"B1": "2"}}, {"t": "d) 289 = 17 to the power __B1__", "a": {"B1": "2"}}, {"t": "e) 400 = 2<sup>m</sup> × 5<sup>n</sup>:  m = __B1__ ,  n = __B2__", "a": {"B1": "4", "B2": "2"}}], "sol": "4 = 2 × 2.\n25 = 5 × 5.\n121 = 11 × 11.\n289 = 17 × 17.\n400 = 2 × 2 × 2 × 2 × 5 × 5 = 2<sup>4</sup> × 5<sup>2</sup>."}, {"kind": "mcq", "text": "<b>Looking Back · Q4</b> · The side of a square measures 5 cm. Its area is", "opts": ["10 cm<sup>2</sup>", "125 cm<sup>2</sup>", "25 cm<sup>2</sup>", "20 cm<sup>2</sup>"], "correct": 2, "tag": "", "sol": "Area = side × side = 5 × 5 = 25 cm<sup>2</sup>. (20 cm is the perimeter, 4 × 5.)"}, {"kind": "blank", "p": "<b>Example 1</b> · Do as directed.", "tag": "", "marks": "", "flat": [{"t": "a) The square of 21 = __B1__", "a": {"B1": "441"}}, {"t": "b) 13<sup>2</sup> = __B1__", "a": {"B1": "169"}}], "sol": "21 × 21 = 441.\n13 × 13 = 169."}, {"kind": "mcq", "text": "<b>Example 2(a)</b> · The square of {−3/2} is", "opts": ["{−9/4}", "{9/4}", "{−3/4}", "{6/4}"], "correct": 1, "tag": "", "sol": "({−3/2})<sup>2</sup> = ((−3) × (−3))/(2 × 2) = {9/4}. The square of a negative number is positive."}, {"kind": "blank", "p": "<b>Example 2(b)</b> · Find the square.", "tag": "", "marks": "", "flat": [{"t": "({5/8})<sup>2</sup> = __B1__", "a": {"B1": "25/64"}, "expr": "fl"}], "sol": "(5 × 5)/(8 × 8) = {25/64}."}, {"kind": "blank", "p": "<b>Example 3</b> · Find the value.", "tag": "", "marks": "", "flat": [{"t": "a) (−5)<sup>2</sup> = __B1__", "a": {"B1": "25"}}, {"t": "b) ({−3/7})<sup>2</sup> = __B1__", "a": {"B1": "9/49"}, "expr": "fl"}], "sol": "(−5) × (−5) = 25.\n((−3) × (−3))/(7 × 7) = {9/49}."}, {"kind": "mcq", "text": "<b>Common Mistake</b> · Which statement is correct?", "opts": ["−3<sup>2</sup> = −9 and (−3)<sup>2</sup> = 9", "−3<sup>2</sup> = 9 and (−3)<sup>2</sup> = 9", "−3<sup>2</sup> = −9 and (−3)<sup>2</sup> = −9", "−3<sup>2</sup> = 9 and (−3)<sup>2</sup> = −9"], "correct": 0, "tag": "", "sol": "In −3<sup>2</sup> only the 3 is squared: −(3 × 3) = −9. In (−3)<sup>2</sup> the whole of −3 is squared: (−3) × (−3) = 9."}, {"kind": "mcq", "text": "<b>Try This (p. 41)</b> · The perfect squares between 100 and 150 are", "opts": ["121, 125 and 144", "121 and 144", "only 121", "110 and 120"], "correct": 1, "tag": "", "sol": "10<sup>2</sup> = 100, 11<sup>2</sup> = 121, 12<sup>2</sup> = 144, 13<sup>2</sup> = 169. So 121 and 144. (125 = 5<sup>3</sup> is a cube, not a square.)"}, {"kind": "blank", "p": "<b>Ex 3A · Q1(a–c)</b> · Find the value.", "tag": "", "marks": "", "flat": [{"t": "a) 18<sup>2</sup> = __B1__", "a": {"B1": "324"}}, {"t": "b) 38<sup>2</sup> = __B1__", "a": {"B1": "1444"}}, {"t": "c) 72<sup>2</sup> = __B1__", "a": {"B1": "5184"}}], "sol": "18 × 18 = 324.\n38 × 38 = 1444.\n72 × 72 = 5184."}, {"kind": "mcq", "text": "<b>Ex 3A · Q1(d)</b> · 7<sup>2</sup> =", "opts": ["14", "42", "77", "49"], "correct": 3, "tag": "", "sol": "7 × 7 = 49. (14 = 7 × 2 doubles instead of squaring.)"}, {"kind": "blank", "p": "<b>Ex 3A · Q1(e, f)</b> · Find the value.", "tag": "", "marks": "", "flat": [{"t": "e) 215<sup>2</sup> = __B1__", "a": {"B1": "46225"}}, {"t": "f) 496<sup>2</sup> = __B1__", "a": {"B1": "246016"}}], "sol": "215 × 215 = 46225 (21 × 22 = 462, then 25).\n496 × 496 = 246016."}, {"kind": "blank", "p": "<b>Ex 3A · Q2(a–c)</b> · Find the square of each number.", "tag": "", "marks": "", "flat": [{"t": "a) {3/8} → __B1__", "a": {"B1": "9/64"}, "expr": "fl"}, {"t": "b) {7/10} → __B1__", "a": {"B1": "49/100"}, "expr": "fl"}, {"t": "c) {3/4} → __B1__", "a": {"B1": "9/16"}, "expr": "fl"}], "sol": "{9/64}.\n{49/100}.\n{9/16}."}, {"kind": "mcq", "text": "<b>Ex 3A · Q2(d)</b> · The square of {1/5} is", "opts": ["{2/10}", "{1/10}", "{1/25}", "{2/5}"], "correct": 2, "tag": "", "sol": "(1 × 1)/(5 × 5) = {1/25}. ({1/10} and {2/5} double instead of squaring.)"}, {"kind": "blank", "p": "<b>Ex 3A · Q2(e, f)</b> · Find the square of each number.", "tag": "", "marks": "", "flat": [{"t": "e) {2/3} → __B1__", "a": {"B1": "4/9"}, "expr": "fl"}, {"t": "f) {31/40} → __B1__", "a": {"B1": "961/1600"}, "expr": "fl"}], "sol": "{4/9}.\n31<sup>2</sup> = 961 and 40<sup>2</sup> = 1600: {961/1600}."}, {"kind": "blank", "p": "<b>Ex 3A · Q3(a–c)</b> · Find the value.", "tag": "", "marks": "", "flat": [{"t": "a) (−3)<sup>2</sup> = __B1__", "a": {"B1": "9"}}, {"t": "b) (−7)<sup>2</sup> = __B1__", "a": {"B1": "49"}}, {"t": "c) (−8)<sup>2</sup> = __B1__", "a": {"B1": "64"}}], "sol": "(−3) × (−3) = 9.\n(−7) × (−7) = 49.\n(−8) × (−8) = 64."}, {"kind": "mcq", "text": "<b>Ex 3A · Q3(d)</b> · ({−2/3})<sup>2</sup> =", "opts": ["{4/6}", "{−4/6}", "{4/9}", "{−4/9}"], "correct": 2, "tag": "", "sol": "((−2) × (−2))/(3 × 3) = {4/9}."}, {"kind": "blank", "p": "<b>Ex 3A · Q3(e–g)</b> · Find the value.", "tag": "", "marks": "", "flat": [{"t": "e) (−0.3)<sup>2</sup> = __B1__", "a": {"B1": "0.09"}, "expr": "dec"}, {"t": "f) (−4)<sup>2</sup> = __B1__", "a": {"B1": "16"}}, {"t": "g) (−0.6)<sup>2</sup> = __B1__", "a": {"B1": "0.36"}, "expr": "dec"}], "sol": "0.3 × 0.3 = 0.09 (1 + 1 = 2 decimal places); the sign becomes +.\n(−4) × (−4) = 16.\n0.6 × 0.6 = 0.36."}, {"kind": "mcq", "text": "<b>Ex 3A · Q3(h)</b> · ({−3/4})<sup>2</sup> =", "opts": ["{−6/8}", "{−9/16}", "{9/16}", "{9/8}"], "correct": 2, "tag": "", "sol": "((−3) × (−3))/(4 × 4) = {9/16}."}, {"kind": "blank", "p": "<b>Ex 3A · Q3(i)</b> · Find the value.", "tag": "", "marks": "", "flat": [{"t": "({−1/2})<sup>2</sup> = __B1__", "a": {"B1": "1/4"}, "expr": "fl"}], "sol": "((−1) × (−1))/(2 × 2) = {1/4}."}]}, {"id": "s2", "label": "3.2 Properties", "sub": "Properties of square numbers — units digits, zeros, odd/even, digits, odd-number sums", "slides": [{"kind": "mcq", "text": "<b>Example 4</b> · By observing only the units digits, which of 3486, 4867 and 8913 can we be sure are NOT perfect squares?", "opts": ["3486 and 4867", "3486 and 8913", "3486 only", "4867 and 8913"], "correct": 3, "tag": "", "sol": "No perfect square ends in 2, 3, 7 or 8. 4867 ends in 7 and 8913 ends in 3, so they cannot be squares. 3486 ends in 6, so the units digit cannot rule it out (4 × 4 and 6 × 6 end in 6). In fact 59<sup>2</sup> = 3481, so 3486 is not a square either, but the units digit alone does not show this."}, {"kind": "blank", "p": "<b>Example 5</b> · Write down the units digit of the square of each number.", "tag": "", "marks": "", "flat": [{"t": "a) 24 → __B1__", "a": {"B1": "6"}}, {"t": "b) 68 → __B1__", "a": {"B1": "4"}}, {"t": "c) 45 → __B1__", "a": {"B1": "5"}}], "sol": "4 × 4 = 16 → 6.\n8 × 8 = 64 → 4.\n5 × 5 = 25 → 5."}, {"kind": "mcq", "text": "Using Property 3, which number is certainly NOT a perfect square?", "opts": ["81,000", "8,10,000", "10,00,000", "8,100"], "correct": 0, "tag": "", "sol": "81,000 ends in an odd number (3) of zeros: 81,000 = 9<sup>2</sup> × 10<sup>2</sup> × 10, and the extra 10 has no partner. 8,100 = 90<sup>2</sup>, 8,10,000 = 900<sup>2</sup>, 10,00,000 = 1000<sup>2</sup>."}, {"kind": "mcq", "text": "<b>Try This (p. 42) · Q1</b> · Can 4368 be a square number?", "opts": ["No, because it is between 4000 and 5000", "Yes, because it is even", "Yes, because its digits add up to 21", "No, because it ends in 8"], "correct": 3, "tag": "", "sol": "A perfect square never has 2, 3, 7 or 8 in its units place. 4368 ends in 8, so it is not a perfect square."}, {"kind": "blank", "p": "<b>Try This (p. 42) · Q2</b> · Find the units digit of the square of each number.", "tag": "", "marks": "", "flat": [{"t": "a) 27 → __B1__", "a": {"B1": "9"}}, {"t": "b) 1234 → __B1__", "a": {"B1": "6"}}, {"t": "c) 2408 → __B1__", "a": {"B1": "4"}}], "sol": "7 × 7 = 49 → 9.\n4 × 4 = 16 → 6.\n8 × 8 = 64 → 4."}, {"kind": "mcq", "text": "Without calculating, 57<sup>2</sup> is", "opts": ["even, because 57<sup>2</sup> has an even exponent", "odd, because every square is odd", "odd, because 57 is odd", "even, because 5 + 7 = 12 is even"], "correct": 2, "tag": "", "sol": "Property 4: the square of an odd number is odd and the square of an even number is even. (57<sup>2</sup> = 3249.)"}, {"kind": "mcq", "text": "<b>Ex 3B · Q1</b> · Observe the units digits. Which of 4836, 8343, 9867, 6384, 3722, 9348 does the units digit show are NOT perfect squares?", "opts": ["8343, 9867, 3722, 9348", "8343, 9867 only", "4836, 3722, 9348", "4836, 6384"], "correct": 0, "tag": "", "sol": "Squares never end in 2, 3, 7 or 8: 8343 (3), 9867 (7), 3722 (2) and 9348 (8) are not perfect squares. 4836 and 6384 end in 6 and 4, so the units digit does not rule them out."}, {"kind": "blank", "p": "<b>Ex 3B · Q2</b> · Write down the units digit of each square.", "tag": "", "marks": "", "flat": [{"t": "a) 78<sup>2</sup> → __B1__", "a": {"B1": "4"}}, {"t": "b) 33<sup>2</sup> → __B1__", "a": {"B1": "9"}}, {"t": "c) 42<sup>2</sup> → __B1__", "a": {"B1": "4"}}, {"t": "d) 35<sup>2</sup> → __B1__", "a": {"B1": "5"}}, {"t": "e) 27<sup>2</sup> → __B1__", "a": {"B1": "9"}}, {"t": "f) 41<sup>2</sup> → __B1__", "a": {"B1": "1"}}], "sol": "8 × 8 = 64 → 4.\n3 × 3 = 9 → 9.\n2 × 2 = 4 → 4.\n5 × 5 = 25 → 5.\n7 × 7 = 49 → 9.\n1 × 1 = 1 → 1."}, {"kind": "blank", "p": "<b>Ex 3B · Q3(a–c)</b> · How many digits does each square have?", "tag": "", "marks": "", "flat": [{"t": "a) 72<sup>2</sup> → __B1__ digits", "a": {"B1": "4"}, "accept": ["four"]}, {"t": "b) 26<sup>2</sup> → __B1__ digits", "a": {"B1": "3"}, "accept": ["three"]}, {"t": "c) 346<sup>2</sup> → __B1__ digits", "a": {"B1": "6"}, "accept": ["six"]}], "sol": "A 2-digit number has a square of 3 or 4 digits: 72<sup>2</sup> = 5184 has 4.\n26<sup>2</sup> = 676 has 3.\nA 3-digit number has a square of 5 or 6 digits: 346<sup>2</sup> = 119716 has 6."}, {"kind": "mcq", "text": "<b>Ex 3B · Q3(d)</b> · The number of digits in 156<sup>2</sup> is", "opts": ["3", "5", "4", "6"], "correct": 1, "tag": "", "sol": "A 3-digit number gives 2 × 3 − 1 = 5 or 2 × 3 = 6 digits. 156<sup>2</sup> = 24336 has 5 digits."}, {"kind": "blank", "p": "<b>Ex 3B · Q3(e, f)</b> · How many digits does each square have?", "tag": "", "marks": "", "flat": [{"t": "e) 3<sup>2</sup> → __B1__ digit(s)", "a": {"B1": "1"}, "accept": ["one"]}, {"t": "f) 9<sup>2</sup> → __B1__ digit(s)", "a": {"B1": "2"}, "accept": ["two"]}], "sol": "3<sup>2</sup> = 9: one digit.\n9<sup>2</sup> = 81: two digits."}, {"kind": "mcq", "text": "15<sup>2</sup> is equal to the sum of", "opts": ["the first 15 odd numbers", "the odd numbers from 1 to 15", "the first 15 even numbers", "the first 15 natural numbers"], "correct": 0, "tag": "", "sol": "Property 6: 1 + 3 + 5 + … (n odd numbers) = n<sup>2</sup>, so 15<sup>2</sup> = 1 + 3 + … + 29. (1 + 3 + … + 15 is only 8 odd numbers = 64.)"}, {"kind": "blank", "p": "<b>Ex 3B · Q4</b> · Find the sum without actually adding the numbers.", "tag": "", "marks": "", "flat": [{"t": "a) 1 + 3 + 5 + 7 + 9 + 11 + 13 + 15 = __B1__", "a": {"B1": "64"}}, {"t": "b) 1 + 3 + 5 + 7 + 9 + 11 + 13 + 15 + 17 = __B1__", "a": {"B1": "81"}}, {"t": "c) 1 + 3 + 5 + 7 = __B1__", "a": {"B1": "16"}}], "sol": "8 odd numbers: 8<sup>2</sup> = 64.\n9 odd numbers: 9<sup>2</sup> = 81.\n4 odd numbers: 4<sup>2</sup> = 16."}, {"kind": "mcq", "text": "<b>Ex 3B · Q5(a)</b> · 7<sup>2</sup> as a sum of consecutive odd numbers starting with 1 is", "opts": ["1 + 3 + 5 + 7 + 9 + 11 + 13 + 15", "1 + 3 + 5 + 7 + 9 + 11 + 13", "1 + 3 + 5 + 7 + 9 + 11", "1 + 3 + 5 + 7"], "correct": 1, "tag": "", "sol": "7<sup>2</sup> is the sum of the first 7 odd numbers; the 7th odd number is 2 × 7 − 1 = 13. Check: 1 + 3 + 5 + 7 + 9 + 11 + 13 = 49."}, {"kind": "blank", "p": "<b>Ex 3B · Q5(b–d)</b> · Express as a sum of consecutive odd numbers starting with 1: write the last odd number.", "tag": "", "marks": "", "flat": [{"t": "b) 81 = 1 + 3 + 5 + … + __B1__", "a": {"B1": "17"}}, {"t": "c) 5<sup>2</sup> = 1 + 3 + … + __B1__", "a": {"B1": "9"}}, {"t": "d) 11<sup>2</sup> = 1 + 3 + 5 + … + __B1__", "a": {"B1": "21"}}], "sol": "81 = 9<sup>2</sup>: 9 odd numbers, the last is 2 × 9 − 1 = 17.\n5 odd numbers: 1 + 3 + 5 + 7 + 9.\n11 odd numbers, the last is 2 × 11 − 1 = 21."}, {"kind": "mcq", "text": "<b>Ex 3B · Q6(a)</b> · How many numbers lie between 4<sup>2</sup> and 5<sup>2</sup>?", "opts": ["9", "10", "8", "7"], "correct": 2, "tag": "", "sol": "Between n<sup>2</sup> and (n + 1)<sup>2</sup> there are 2n numbers: 2 × 4 = 8 (17, 18, …, 24)."}, {"kind": "blank", "p": "<b>Ex 3B · Q6(b–d)</b> · State the number of numbers between:", "tag": "", "marks": "", "flat": [{"t": "b) 15<sup>2</sup> and 16<sup>2</sup> → __B1__", "a": {"B1": "30"}}, {"t": "c) 10<sup>2</sup> and 11<sup>2</sup> → __B1__", "a": {"B1": "20"}}, {"t": "d) 30<sup>2</sup> and 31<sup>2</sup> → __B1__", "a": {"B1": "60"}}], "sol": "2 × 15 = 30.\n2 × 10 = 20.\n2 × 30 = 60."}, {"kind": "blank", "p": "<b>Ex 3B · Q12(a–c)</b> · These are all perfect squares. Without calculating, is each the square of an odd or an even number? (type odd or even)", "tag": "", "marks": "", "flat": [{"t": "a) 961 → __B1__", "a": {"B1": "odd"}, "expr": "words"}, {"t": "b) 313600 → __B1__", "a": {"B1": "even"}, "expr": "words"}, {"t": "c) 529 → __B1__", "a": {"B1": "odd"}, "expr": "words"}], "sol": "961 is odd, so it is the square of an odd number (31<sup>2</sup>).\n313600 is even, so it is the square of an even number (560<sup>2</sup>).\n529 is odd (23<sup>2</sup>)."}, {"kind": "mcq", "text": "<b>Ex 3B · Q12(d)</b> · 6724 is a perfect square. It is the square of", "opts": ["an even number, because 6724 is even", "an odd number, because it has four digits", "an odd number, because 67 + 24 = 91 is odd", "an odd number, because 6 + 7 + 2 + 4 = 19 is odd"], "correct": 0, "tag": "", "sol": "Even squares come only from even numbers (Property 4): 6724 = 82<sup>2</sup>."}, {"kind": "blank", "p": "<b>Ex 3B · Q12(e, f)</b> · Odd or even number? (type odd or even)", "tag": "", "marks": "", "flat": [{"t": "e) 1089 → __B1__", "a": {"B1": "odd"}, "expr": "words"}, {"t": "f) 4225 → __B1__", "a": {"B1": "odd"}, "expr": "words"}], "sol": "1089 is odd (33<sup>2</sup>).\n4225 is odd (65<sup>2</sup>)."}]}, {"id": "s3", "label": "3.3 Triplets & patterns", "sub": "Pythagorean triplets, triangular numbers, square patterns and squaring numbers ending in 5", "slides": [{"kind": "blank", "p": "<b>Looking Back · Q5</b> · Triangle ABC is right-angled at C. BC = 3 cm and CA = 4 cm. Find BA.", "tag": "", "marks": "", "flat": [{"t": "BA<sup>2</sup> = __B1__", "a": {"B1": "25"}}, {"t": "BA = __B1__ cm", "a": {"B1": "5"}}], "sol": "BA is the hypotenuse: BA<sup>2</sup> = 3<sup>2</sup> + 4<sup>2</sup> = 9 + 16 = 25.\nBA = √25 = 5 cm.", "fig": "<svg class=\"figsvg\" viewBox=\"0 0 300 170\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><line class=\"ln\" x1=\"30.0\" y1=\"140.0\" x2=\"215.0\" y2=\"140.0\"/><line class=\"ln\" x1=\"215.0\" y1=\"140.0\" x2=\"215.0\" y2=\"30.0\"/><line class=\"ln\" x1=\"30.0\" y1=\"140.0\" x2=\"215.0\" y2=\"30.0\"/><path class=\"ra\" d=\"M215.0,129.0 L204.0,129.0 L204.0,140.0\"/><text class=\"lb\" x=\"122.0\" y=\"157.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">CA = 4 cm</text><text class=\"lb\" x=\"222.0\" y=\"85.0\" text-anchor=\"start\" dominant-baseline=\"middle\">BC = 3 cm</text><text class=\"al\" x=\"108.0\" y=\"70.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">BA = ?</text><text class=\"lb\" x=\"18.0\" y=\"144.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">A</text><text class=\"lb\" x=\"225.0\" y=\"150.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">C</text><text class=\"lb\" x=\"225.0\" y=\"24.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">B</text></svg>"}, {"kind": "mcq", "text": "Which set is a Pythagorean triplet?", "opts": ["2, 3, 4", "5, 12, 14", "5, 12, 13", "4, 6, 8"], "correct": 2, "tag": "", "sol": "5<sup>2</sup> + 12<sup>2</sup> = 25 + 144 = 169 = 13<sup>2</sup>. For 5, 12, 14: 169 ≠ 196; 4, 6, 8: 52 ≠ 64; 2, 3, 4: 13 ≠ 16."}, {"kind": "blank", "p": "Use the formula 2m, m<sup>2</sup> − 1, m<sup>2</sup> + 1 with m = 5 to make a Pythagorean triplet.", "tag": "", "marks": "", "flat": [{"t": "2m = __B1__", "a": {"B1": "10"}}, {"t": "m<sup>2</sup> − 1 = __B1__", "a": {"B1": "24"}}, {"t": "m<sup>2</sup> + 1 = __B1__", "a": {"B1": "26"}}], "sol": "2 × 5 = 10.\n25 − 1 = 24.\n25 + 1 = 26. Check: 100 + 576 = 676 = 26<sup>2</sup>."}, {"kind": "mcq", "text": "The nth triangular number is n(n + 1)/2. The 10th triangular number is", "opts": ["100", "55", "110", "45"], "correct": 1, "tag": "", "sol": "10 × 11 ÷ 2 = 110 ÷ 2 = 55. (110 forgets to halve, 45 is the 9th triangular number and 100 is 10<sup>2</sup>.)"}, {"kind": "blank", "p": "<b>Example 6</b> · Use n<sup>2</sup> = 2(n − 1)<sup>2</sup> − (n − 2)<sup>2</sup> + 2 to find 10<sup>2</sup>.", "tag": "", "marks": "", "flat": [{"t": "2(9)<sup>2</sup> = __B1__", "a": {"B1": "162"}}, {"t": "8<sup>2</sup> = __B1__", "a": {"B1": "64"}}, {"t": "10<sup>2</sup> = 162 − 64 + 2 = __B1__", "a": {"B1": "100"}}], "sol": "2 × 81 = 162.\n8 × 8 = 64.\n162 − 64 + 2 = 100."}, {"kind": "mcq", "text": "<b>Example 7</b> · Using n<sup>2</sup> = 2(1 + 2 + … + (n − 1)) + n, which working gives 10<sup>2</sup>?", "opts": ["2 × 45 + 9 = 99", "2 × 36 + 10 = 82", "2 × 55 + 10 = 120", "2 × 45 + 10 = 100"], "correct": 3, "tag": "", "sol": "For n = 10: 1 + 2 + … + 9 = 45, so 10<sup>2</sup> = 2 × 45 + 10 = 100. (1 + … + 10 = 55 goes one term too far.)"}, {"kind": "blank", "p": "<b>Example 8</b> · Use n<sup>2</sup> = (n − 1)(n + 1) + 1.", "tag": "", "marks": "", "flat": [{"t": "31<sup>2</sup> = 30 × 32 + 1 = __B1__", "a": {"B1": "961"}}], "sol": "30 × 32 = 960; 960 + 1 = 961."}, {"kind": "blank", "p": "<b>Ex 3B · Q7</b> · State the 5th and 6th terms of triangular numbers. What square number do we get if we add them?", "tag": "", "marks": "", "flat": [{"t": "5th term = __B1__", "a": {"B1": "15"}}, {"t": "6th term = __B1__", "a": {"B1": "21"}}, {"t": "Sum = __B1__", "a": {"B1": "36"}}], "sol": "5 × 6 ÷ 2 = 15.\n6 × 7 ÷ 2 = 21.\n15 + 21 = 36 = 6<sup>2</sup>, the square of the higher term number."}, {"kind": "mcq", "text": "<b>Ex 3B · Q8(a)</b> · Adding the 8th and 9th triangular numbers gives", "opts": ["90", "72", "64", "81"], "correct": 3, "tag": "", "sol": "8th = 36, 9th = 45; 36 + 45 = 81 = 9<sup>2</sup> (square of the higher term number)."}, {"kind": "blank", "p": "<b>Ex 3B · Q8(b)</b> · What square number do we get if we add the 13th and 14th triangular numbers?", "tag": "", "marks": "", "flat": [{"t": "13th + 14th = __B1__", "a": {"B1": "196"}}], "sol": "13th = 91, 14th = 105; 91 + 105 = 196 = 14<sup>2</sup>."}, {"kind": "mcq", "text": "<b>Ex 3B · Q9</b> · Which of these form Pythagorean triplets?  (a) 4, 5, 6   (b) 6, 8, 10   (c) 24, 10, 26   (d) 7, 8, 10", "opts": ["(b) and (c)", "(a) and (d)", "(b), (c) and (d)", "(b) only"], "correct": 0, "tag": "", "sol": "(b) 36 + 64 = 100 = 10<sup>2</sup> ✓. (c) 100 + 576 = 676 = 26<sup>2</sup> ✓. (a) 16 + 25 = 41 ≠ 36. (d) 49 + 64 = 113 ≠ 100."}, {"kind": "blank", "p": "<b>Ex 3B · Q10</b> · What will be the length of the diagonal of a rectangle of sides 6 m and 8 m?", "tag": "", "marks": "", "flat": [{"t": "Diagonal = __B1__ m", "a": {"B1": "10"}}], "sol": "The diagonal is the hypotenuse: 6<sup>2</sup> + 8<sup>2</sup> = 36 + 64 = 100, so the diagonal = √100 = 10 m.", "fig": "<svg class=\"figsvg\" viewBox=\"0 0 300 160\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><rect class=\"sh3\" x=\"50\" y=\"30\" width=\"200\" height=\"100\"/><line class=\"ln hid\" x1=\"50.0\" y1=\"130.0\" x2=\"250.0\" y2=\"30.0\"/><text class=\"lb\" x=\"150.0\" y=\"147.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">8 m</text><text class=\"lb\" x=\"258.0\" y=\"80.0\" text-anchor=\"start\" dominant-baseline=\"middle\">6 m</text><text class=\"al\" x=\"138.0\" y=\"68.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">?</text></svg>"}, {"kind": "mcq", "text": "<b>Ex 3B · Q11(a)</b> · Using the method for a 2-digit number with units digit 5, 45<sup>2</sup> =", "opts": ["2045", "2025", "1625", "2525"], "correct": 1, "tag": "", "sol": "4 × 5 = 20; write 25 after it: 2025. (1625 uses 4 × 4, and 2525 writes 25 twice.)"}, {"kind": "blank", "p": "<b>Ex 3B · Q11(b–e)</b> · Find the squares using the method for numbers with units digit 5.", "tag": "", "marks": "", "flat": [{"t": "b) 75<sup>2</sup> = __B1__", "a": {"B1": "5625"}}, {"t": "c) 95<sup>2</sup> = __B1__", "a": {"B1": "9025"}}, {"t": "d) 25<sup>2</sup> = __B1__", "a": {"B1": "625"}}, {"t": "e) 65<sup>2</sup> = __B1__", "a": {"B1": "4225"}}], "sol": "7 × 8 = 56 → 5625.\n9 × 10 = 90 → 9025.\n2 × 3 = 6 → 625.\n6 × 7 = 42 → 4225."}]}, {"id": "s4", "label": "3.4 Roots by factors", "sub": "Square roots of perfect squares and algebraic terms by prime factorisation", "slides": [{"kind": "blank", "p": "<b>Example 9</b> · Give the positive square root.", "tag": "", "marks": "", "flat": [{"t": "a) The square root of 36 = __B1__", "a": {"B1": "6"}}, {"t": "b) √64 = __B1__", "a": {"B1": "8"}}], "sol": "36 = 6 × 6, so √36 = 6.\n64 = 8 × 8, so √64 = 8."}, {"kind": "mcq", "text": "Which numbers have 25 as their square?", "opts": ["only −5", "5 and −5", "only 5", "12.5 and −12.5"], "correct": 1, "tag": "", "sol": "5 × 5 = 25 and (−5) × (−5) = 25, so 25 has two square roots, 5 and −5. The symbol √25 means the positive one, 5."}, {"kind": "blank", "p": "<b>Example 10</b> · Find the square root of 144 by prime factorisation.", "tag": "", "marks": "", "flat": [{"t": "144 = 2<sup>m</sup> × 3<sup>n</sup>:  m = __B1__ ,  n = __B2__", "a": {"B1": "4", "B2": "2"}}, {"t": "√144 = __B1__", "a": {"B1": "12"}}], "sol": "144 = 2 × 2 × 2 × 2 × 3 × 3.\nOne factor from each pair: 2 × 2 × 3 = 12."}, {"kind": "mcq", "text": "<b>Example 11</b> · By prime factorisation, √400 =", "opts": ["200", "40", "16", "20"], "correct": 3, "tag": "", "sol": "400 = (2 × 2) × (2 × 2) × (5 × 5); one from each pair: 2 × 2 × 5 = 20."}, {"kind": "blank", "p": "<b>Example 12</b> · Find √729 using prime factorisation.", "tag": "", "marks": "", "flat": [{"t": "729 = 3 to the power __B1__", "a": {"B1": "6"}}, {"t": "√729 = __B1__", "a": {"B1": "27"}}], "sol": "729 = 3 × 3 × 3 × 3 × 3 × 3 = 3<sup>6</sup>.\nThree pairs of 3: 3 × 3 × 3 = 27."}, {"kind": "mcq", "text": "<b>Example 13</b> · The square root of 324 is", "opts": ["16", "24", "162", "18"], "correct": 3, "tag": "", "sol": "324 = (2 × 2) × (3 × 3) × (3 × 3); √324 = 2 × 3 × 3 = 18."}, {"kind": "blank", "p": "<b>Example 14</b> · Find the square root of 2 × 2 × 2 × 2 × 3 × 3 × 5 × 5.", "tag": "", "marks": "", "flat": [{"t": "Square root = __B1__", "a": {"B1": "60"}}], "sol": "Pairs: (2 × 2)(2 × 2)(3 × 3)(5 × 5); one from each: 2 × 2 × 3 × 5 = 60."}, {"kind": "blank", "p": "<b>Example 15</b> · Find the square root of 1764 by finding prime factors.", "tag": "", "marks": "", "flat": [{"t": "1764 = 2<sup>2</sup> × 3<sup>m</sup> × 7<sup>n</sup>:  m = __B1__ ,  n = __B2__", "a": {"B1": "2", "B2": "2"}}, {"t": "√1764 = __B1__", "a": {"B1": "42"}}], "sol": "1764 = 2 × 2 × 3 × 3 × 7 × 7.\n2 × 3 × 7 = 42."}, {"kind": "mcq", "text": "<b>Example 16</b> · √(9a<sup>4</sup>b<sup>8</sup>) =", "opts": ["3a<sup>2</sup>b<sup>6</sup>", "3a<sup>2</sup>b<sup>4</sup>", "3a<sup>4</sup>b<sup>8</sup>", "9a<sup>2</sup>b<sup>4</sup>"], "correct": 1, "tag": "", "sol": "9 = 3 × 3, a<sup>4</sup> = a<sup>2</sup> × a<sup>2</sup>, b<sup>8</sup> = b<sup>4</sup> × b<sup>4</sup>: take one of each pair, 3a<sup>2</sup>b<sup>4</sup>."}, {"kind": "blank", "p": "Find √36 by repeated subtraction of odd numbers: 36 − 1 − 3 − 5 − …", "tag": "", "marks": "", "flat": [{"t": "Last odd number subtracted = __B1__", "a": {"B1": "11"}}, {"t": "Number of subtractions = √36 = __B1__", "a": {"B1": "6"}}], "sol": "36 − 1 = 35, − 3 = 32, − 5 = 27, − 7 = 20, − 9 = 11, − 11 = 0.\nSix subtractions, so √36 = 6."}, {"kind": "blank", "p": "<b>Mental Maths (p. 46)</b> · Find the square roots.", "tag": "", "marks": "", "flat": [{"t": "√36 = __B1__", "a": {"B1": "6"}}, {"t": "√81 = __B1__", "a": {"B1": "9"}}, {"t": "√100 = __B1__", "a": {"B1": "10"}}, {"t": "√9 = __B1__", "a": {"B1": "3"}}, {"t": "√25 = __B1__", "a": {"B1": "5"}}, {"t": "√121 = __B1__", "a": {"B1": "11"}}], "sol": "6 × 6 = 36.\n9 × 9 = 81.\n10 × 10 = 100.\n3 × 3 = 9.\n5 × 5 = 25.\n11 × 11 = 121."}, {"kind": "mcq", "text": "<b>Project (a)</b> · In a factor chart of the numbers 1 to 25, which are the square numbers?", "opts": ["4, 9, 16", "2, 4, 8, 16", "1, 3, 6, 10, 15, 21", "1, 4, 9, 16, 25"], "correct": 3, "tag": "", "sol": "1 = 1<sup>2</sup>, 4 = 2<sup>2</sup>, 9 = 3<sup>2</sup>, 16 = 4<sup>2</sup>, 25 = 5<sup>2</sup>. In the chart they are the only numbers with an odd number of factors (1, 3, 3, 5, 3 factors)."}, {"kind": "mcq", "text": "<b>Project (b)</b> · What do you observe about the factors of square numbers?", "opts": ["They have an odd number of factors", "All their factors are odd", "They have an even number of factors", "They have exactly two factors"], "correct": 0, "tag": "", "sol": "Factors come in pairs (a × b), but for a square one pair is a number times itself, counted once: 16 has 1, 2, 4, 8, 16 — five factors."}, {"kind": "blank", "p": "<b>Ex 3C · Q1(a–d)</b> · Fill in the blanks.", "tag": "", "marks": "", "flat": [{"t": "a) If 8 × 8 = 64, then √64 is __B1__", "a": {"B1": "8"}}, {"t": "b) If 11 × 11 is 121, then √121 is __B1__", "a": {"B1": "11"}}, {"t": "c) If 25 × 25 is 625, then √625 is __B1__", "a": {"B1": "25"}}, {"t": "d) If (2 × 9) × (2 × 9) is 324, then √324 is __B1__", "a": {"B1": "18"}}], "sol": "8.\n11.\n25.\n2 × 9 = 18."}, {"kind": "mcq", "text": "<b>Ex 3C · Q1(e)</b> · If 15<sup>2</sup> is 225, then √225 is", "opts": ["5", "112.5", "25", "15"], "correct": 3, "tag": "", "sol": "Square root undoes squaring: √225 = 15."}, {"kind": "blank", "p": "<b>Ex 3C · Q1(f, g)</b> · Fill in the blanks.", "tag": "", "marks": "", "flat": [{"t": "f) If (2 × 3 × 5) × (2 × 3 × 5) is 900, then √900 is __B1__", "a": {"B1": "30"}}, {"t": "g) If (7 × 11 × 13)<sup>2</sup> = 1002001, then √1002001 is __B1__", "a": {"B1": "1001"}}], "sol": "2 × 3 × 5 = 30.\n7 × 11 × 13 = 1001."}, {"kind": "blank", "p": "<b>Ex 3C · Q2(a–c)</b> · State the number of digits in the square root of each number.", "tag": "", "marks": "", "flat": [{"t": "a) 529 → __B1__", "a": {"B1": "2"}, "accept": ["two"]}, {"t": "b) 5041 → __B1__", "a": {"B1": "2"}, "accept": ["two"]}, {"t": "c) 4 → __B1__", "a": {"B1": "1"}, "accept": ["one"]}], "sol": "5|29: 2 bars → 2 digits (√529 = 23).\n50|41: 2 bars → 2 digits (71).\nOne bar → 1 digit (2)."}, {"kind": "mcq", "text": "<b>Ex 3C · Q2(d)</b> · The square root of 15129 has how many digits?", "opts": ["4", "3", "2", "5"], "correct": 1, "tag": "", "sol": "Bars from the units digit: 1|51|29 → 3 bars, so 3 digits (√15129 = 123)."}, {"kind": "blank", "p": "<b>Ex 3C · Q2(e, f)</b> · State the number of digits in the square root.", "tag": "", "marks": "", "flat": [{"t": "e) 848241 → __B1__", "a": {"B1": "3"}, "accept": ["three"]}, {"t": "f) 36 → __B1__", "a": {"B1": "1"}, "accept": ["one"]}], "sol": "84|82|41: 3 bars (√848241 = 921).\nOne bar: 1 digit (6)."}, {"kind": "blank", "p": "<b>Ex 3C · Q3(a–c)</b> · Find the square root.", "tag": "", "marks": "", "flat": [{"t": "a) 2 × 2 × 3 × 3 × 4 × 4 → __B1__", "a": {"B1": "24"}}, {"t": "b) 3 × 3 × 3 × 3 × 5 × 5 → __B1__", "a": {"B1": "45"}}, {"t": "c) 7 × 7 × 3 × 3 × 2 × 2 × 2 × 2 → __B1__", "a": {"B1": "84"}}], "sol": "2 × 3 × 4 = 24.\n3 × 3 × 5 = 45.\n7 × 3 × 2 × 2 = 84."}, {"kind": "mcq", "text": "<b>Ex 3C · Q3(d)</b> · The square root of 64x<sup>2</sup>y<sup>4</sup> is", "opts": ["32xy<sup>2</sup>", "8xy<sup>2</sup>", "8x<sup>2</sup>y<sup>4</sup>", "8xy<sup>4</sup>"], "correct": 1, "tag": "", "sol": "64 = 8 × 8, x<sup>2</sup> = x × x, y<sup>4</sup> = y<sup>2</sup> × y<sup>2</sup>: √ = 8xy<sup>2</sup>."}, {"kind": "mcq", "text": "<b>Ex 3C · Q3(e)</b> · The square root of 144a<sup>4</sup>b<sup>2</sup>c<sup>2</sup> is", "opts": ["12a<sup>4</sup>bc", "72a<sup>2</sup>bc", "12a<sup>2</sup>b<sup>2</sup>c<sup>2</sup>", "12a<sup>2</sup>bc"], "correct": 3, "tag": "", "sol": "144 = 12 × 12, a<sup>4</sup> = a<sup>2</sup> × a<sup>2</sup>, b<sup>2</sup> = b × b, c<sup>2</sup> = c × c: 12a<sup>2</sup>bc."}, {"kind": "blank", "p": "<b>Ex 3C · Q4(a–e)</b> · Find the square root by prime factorisation.", "tag": "", "marks": "", "flat": [{"t": "a) √3969 = __B1__", "a": {"B1": "63"}}, {"t": "b) √7744 = __B1__", "a": {"B1": "88"}}, {"t": "c) √4356 = __B1__", "a": {"B1": "66"}}, {"t": "d) √5184 = __B1__", "a": {"B1": "72"}}, {"t": "e) √784 = __B1__", "a": {"B1": "28"}}], "sol": "3969 = 3<sup>4</sup> × 7<sup>2</sup> → 3 × 3 × 7 = 63.\n7744 = 2<sup>6</sup> × 11<sup>2</sup> → 2 × 2 × 2 × 11 = 88.\n4356 = 2<sup>2</sup> × 3<sup>2</sup> × 11<sup>2</sup> → 2 × 3 × 11 = 66.\n5184 = 2<sup>6</sup> × 3<sup>4</sup> → 8 × 9 = 72.\n784 = 2<sup>4</sup> × 7<sup>2</sup> → 4 × 7 = 28."}, {"kind": "mcq", "text": "<b>Ex 3C · Q4(f)</b> · By prime factorisation, √7056 =", "opts": ["94", "86", "74", "84"], "correct": 3, "tag": "", "sol": "7056 = 2<sup>4</sup> × 3<sup>2</sup> × 7<sup>2</sup>, so √7056 = 2 × 2 × 3 × 7 = 84."}, {"kind": "blank", "p": "<b>Ex 3C · Q4(g–j)</b> · Find the square root by prime factorisation.", "tag": "", "marks": "", "flat": [{"t": "g) √5625 = __B1__", "a": {"B1": "75"}}, {"t": "h) √4624 = __B1__", "a": {"B1": "68"}}, {"t": "i) √291600 = __B1__", "a": {"B1": "540"}}, {"t": "j) √108900 = __B1__", "a": {"B1": "330"}}], "sol": "5625 = 3<sup>2</sup> × 5<sup>4</sup> → 3 × 25 = 75.\n4624 = 2<sup>4</sup> × 17<sup>2</sup> → 4 × 17 = 68.\n291600 = 2<sup>4</sup> × 3<sup>6</sup> × 5<sup>2</sup> → 4 × 27 × 5 = 540.\n108900 = 2<sup>2</sup> × 3<sup>2</sup> × 5<sup>2</sup> × 11<sup>2</sup> → 2 × 3 × 5 × 11 = 330."}, {"kind": "mcq", "text": "<b>Ex 3C · Q5(a)</b> · Simplify √(a<sup>2</sup> × b<sup>4</sup>).", "opts": ["ab<sup>2</sup>", "a<sup>2</sup>b<sup>2</sup>", "a<sup>2</sup>b", "ab<sup>4</sup>"], "correct": 0, "tag": "", "sol": "Halve each exponent: a<sup>1</sup>b<sup>2</sup> = ab<sup>2</sup>."}, {"kind": "blank", "p": "<b>Ex 3C · Q5(b, c)</b> · Simplify.", "tag": "", "marks": "", "flat": [{"t": "b) √(2<sup>12</sup>) = __B1__", "a": {"B1": "64"}}, {"t": "c) √(2<sup>8</sup> × 3<sup>4</sup>) = __B1__", "a": {"B1": "144"}}], "sol": "√(2<sup>12</sup>) = 2<sup>6</sup> = 64.\n2<sup>4</sup> × 3<sup>2</sup> = 16 × 9 = 144."}, {"kind": "mcq", "text": "<b>Ex 3C · Q5(d)</b> · Simplify √(49x<sup>2</sup>y<sup>2</sup>).", "opts": ["49xy", "7xy", "24.5xy", "7x<sup>2</sup>y<sup>2</sup>"], "correct": 1, "tag": "", "sol": "49 = 7 × 7, x<sup>2</sup> = x × x, y<sup>2</sup> = y × y: 7xy."}, {"kind": "blank", "p": "<b>Ex 3C · Q5(e, f)</b> · Simplify.", "tag": "", "marks": "", "flat": [{"t": "e) √(16a<sup>6</sup>) = k a<sup>n</sup>:  k = __B1__ ,  n = __B2__", "a": {"B1": "4", "B2": "3"}}, {"t": "f) √(a<sup>4</sup>b<sup>6</sup>) = a<sup>m</sup>b<sup>n</sup>:  m = __B1__ ,  n = __B2__", "a": {"B1": "2", "B2": "3"}}], "sol": "√16 = 4 and a<sup>6</sup> = a<sup>3</sup> × a<sup>3</sup>: 4a<sup>3</sup>.\na<sup>2</sup>b<sup>3</sup>."}, {"kind": "mcq", "text": "<b>Ex 3C · Q6</b> · What is the side of a square room whose area is 144 sq. m?", "opts": ["36 m", "12 m", "72 m", "14 m"], "correct": 1, "tag": "", "sol": "Side = √144 = 12 m. (36 m = 144 ÷ 4 confuses area with perimeter.)"}, {"kind": "blank", "p": "<b>Ex 3C · Q7</b> · Find the length of the other side of a right-angled triangle if one side is 12 cm and the hypotenuse is 13 cm.", "tag": "", "marks": "", "flat": [{"t": "(other side)<sup>2</sup> = 13<sup>2</sup> − 12<sup>2</sup> = __B1__", "a": {"B1": "25"}}, {"t": "Other side = __B1__ cm", "a": {"B1": "5"}}], "sol": "169 − 144 = 25.\n√25 = 5 cm.", "fig": "<svg class=\"figsvg\" viewBox=\"0 0 300 170\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><line class=\"ln\" x1=\"30.0\" y1=\"140.0\" x2=\"215.0\" y2=\"140.0\"/><line class=\"ln\" x1=\"215.0\" y1=\"140.0\" x2=\"215.0\" y2=\"30.0\"/><line class=\"ln\" x1=\"30.0\" y1=\"140.0\" x2=\"215.0\" y2=\"30.0\"/><path class=\"ra\" d=\"M215.0,129.0 L204.0,129.0 L204.0,140.0\"/><text class=\"lb\" x=\"122.0\" y=\"157.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">? cm</text><text class=\"lb\" x=\"222.0\" y=\"85.0\" text-anchor=\"start\" dominant-baseline=\"middle\">12 cm</text><text class=\"al\" x=\"108.0\" y=\"70.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">13 cm</text></svg>"}]}, {"id": "s5", "label": "3.5 Division method", "sub": "Square roots by the long division method; rational numbers, decimals and approximate roots", "slides": [{"kind": "blank", "p": "<b>Example 17</b> · Find the square root of 225 by the division method (periods 2 | 25).", "tag": "", "marks": "", "flat": [{"t": "First digit of the root = __B1__", "a": {"B1": "1"}}, {"t": "Second divisor = 2_ × _: the divisor is __B1__", "a": {"B1": "25"}}, {"t": "√225 = __B1__", "a": {"B1": "15"}}], "sol": "1<sup>2</sup> = 1 ≤ 2; remainder 1, bring down 25 → 125.\nDouble 1 → 2_; 25 × 5 = 125.\nRemainder 0, so √225 = 15."}, {"kind": "mcq", "text": "<b>Example 18</b> · 2916 lies between 50<sup>2</sup> = 2500 and 60<sup>2</sup> = 3600 and ends in 6. By the division method, √2916 =", "opts": ["46", "56", "64", "54"], "correct": 3, "tag": "", "sol": "Periods 29 | 16: 5<sup>2</sup> = 25, remainder 4; bring down 16 → 416; 104 × 4 = 416, remainder 0. So √2916 = 54 (56<sup>2</sup> = 3136)."}, {"kind": "blank", "p": "<b>Example 19</b> · Find the square root of 274576 (periods 27 | 45 | 76).", "tag": "", "marks": "", "flat": [{"t": "First divisor and digit = __B1__", "a": {"B1": "5"}}, {"t": "Second divisor = __B1__", "a": {"B1": "102"}}, {"t": "Third divisor = __B1__", "a": {"B1": "1044"}}, {"t": "√274576 = __B1__", "a": {"B1": "524"}}], "sol": "5<sup>2</sup> = 25 ≤ 27, remainder 2; bring down 45 → 245.\nDouble 5 → 10_: 102 × 2 = 204 (103 × 3 = 309 is too big); remainder 41, bring down 76 → 4176.\nDouble 52 → 104_: 1044 × 4 = 4176.\nRemainder 0: √274576 = 524."}, {"kind": "mcq", "text": "How many digits does the square root of 274576 have?", "opts": ["4", "2", "3", "6"], "correct": 2, "tag": "", "sol": "Pairs from the right: 27|45|76 — three periods, so the root has 3 digits (524)."}, {"kind": "mcq", "text": "<b>Example 20</b> · The square root of {64/144} is", "opts": ["{4/9}", "{32/72}", "{8/14}", "{2/3}"], "correct": 3, "tag": "", "sol": "√64 = 8 and √144 = 12, so the root is {8/12} = {2/3}. ({4/9} is the fraction itself in lowest terms, not its root.)"}, {"kind": "blank", "p": "<b>Example 21</b> · Find the square root of {17 137/256}.", "tag": "", "marks": "", "flat": [{"t": "{17 137/256} as an improper fraction = __B1__", "a": {"B1": "4489/256"}, "expr": "fl"}, {"t": "Square root = __B1__", "a": {"B1": "67/16"}, "expr": "fv"}], "sol": "17 × 256 + 137 = 4489, so {4489/256}.\n√4489 = 67 and √256 = 16: {67/16} = {4 3/16}."}, {"kind": "blank", "p": "<b>Example 22(a)</b> · For the division method the number 73468.7345 is paired as 7 | 34 | 68 . 73 | 45.", "tag": "", "marks": "", "flat": [{"t": "Number of periods in the whole-number part = __B1__", "a": {"B1": "3"}}, {"t": "Number of digits before the decimal point in its square root = __B1__", "a": {"B1": "3"}}], "sol": "Pairs are made from the decimal point to the left: 68, 34 and the single 7 (a leftover digit on the left is a period on its own), so 3 periods.\nEach period of the whole-number part gives one digit of the root, so 3 digits before the point. The decimal part 73 45 is paired from the point to the right."}, {"kind": "mcq", "text": "<b>Example 22(b)</b> · The correct pairing of 6734.834 for the division method is", "opts": ["673 4 . 834 0", "67 34 . 83 40", "67 34 . 8 34", "6 73 . 48 34"], "correct": 1, "tag": "", "sol": "Whole-number part: pairs from the right (67 34). Decimal part: pairs from the left, adding a zero to finish the last pair (83 40). Similarly 73468.7345 → 7 34 68 . 73 45."}, {"kind": "blank", "p": "<b>Example 23</b> · Find the square root of 3180.96.", "tag": "", "marks": "", "flat": [{"t": "Second divisor = __B1__", "a": {"B1": "106"}}, {"t": "√3180.96 = __B1__", "a": {"B1": "56.4"}, "expr": "dec"}], "sol": "5<sup>2</sup> = 25 ≤ 31, remainder 6; bring down 80 → 680; 106 × 6 = 636.\nRemainder 44, bring down 96 → 4496; 1124 × 4 = 4496. The point comes after 56: √3180.96 = 56.4."}, {"kind": "blank", "p": "<b>Example 24</b> · Find the square root of 7896 correct up to two decimal places.", "tag": "", "marks": "", "flat": [{"t": "√7896 to 3 decimal places = __B1__", "a": {"B1": "88.859"}, "expr": "dec"}, {"t": "Correct to 2 decimal places = __B1__", "a": {"B1": "88.86"}, "expr": "dec"}], "sol": "Add zeros: 78 96 . 00 00 00. Divisors 8, 168, 1768, 17765, 177709 give 88.859.\nThe third decimal 9 ≥ 5, so round up: 88.86."}, {"kind": "mcq", "text": "<b>Try This (p. 50) · Q1</b> · The square root of 13.69 is", "opts": ["37", "6.845", "3.7", "0.37"], "correct": 2, "tag": "", "sol": "Pairs 13 . 69: 3<sup>2</sup> = 9, remainder 4; bring down 69 → 469; 67 × 7 = 469, remainder 0. The point comes after the first digit, so √13.69 = 3.7. (6.845 halves the number instead of taking its root.)"}, {"kind": "blank", "p": "<b>Ex 3D · Q1(a–c)</b> · Find the square root by the division method.", "tag": "", "marks": "", "flat": [{"t": "a) √3969 = __B1__", "a": {"B1": "63"}}, {"t": "b) √54289 = __B1__", "a": {"B1": "233"}}, {"t": "c) √8281 = __B1__", "a": {"B1": "91"}}], "sol": "a) 6<sup>2</sup> = 36 ≤ 39, remainder 3; bring down → 369; 123 × 3 = 369, remainder 0. So √3969 = 63.\nb) 2<sup>2</sup> = 4 ≤ 5, remainder 1; bring down → 142; 43 × 3 = 129, remainder 13; bring down → 1389; 463 × 3 = 1389, remainder 0. So √54289 = 233.\nc) 9<sup>2</sup> = 81 ≤ 82, remainder 1; bring down → 181; 181 × 1 = 181, remainder 0. So √8281 = 91."}, {"kind": "mcq", "text": "<b>Ex 3D · Q1(d)</b> · By the division method, √53361 =", "opts": ["221", "213", "241", "231"], "correct": 3, "tag": "", "sol": "2<sup>2</sup> = 4 ≤ 5, remainder 1; bring down → 133; 43 × 3 = 129, remainder 4; bring down → 461; 461 × 1 = 461, remainder 0. So √53361 = 231."}, {"kind": "blank", "p": "<b>Ex 3D · Q1(e–g)</b> · Find the square root by the division method.", "tag": "", "marks": "", "flat": [{"t": "e) √6889 = __B1__", "a": {"B1": "83"}}, {"t": "f) √2116 = __B1__", "a": {"B1": "46"}}, {"t": "g) √423801 = __B1__", "a": {"B1": "651"}}], "sol": "e) 8<sup>2</sup> = 64 ≤ 68, remainder 4; bring down → 489; 163 × 3 = 489, remainder 0. So √6889 = 83.\nf) 4<sup>2</sup> = 16 ≤ 21, remainder 5; bring down → 516; 86 × 6 = 516, remainder 0. So √2116 = 46.\ng) 6<sup>2</sup> = 36 ≤ 42, remainder 6; bring down → 638; 125 × 5 = 625, remainder 13; bring down → 1301; 1301 × 1 = 1301, remainder 0. So √423801 = 651."}, {"kind": "mcq", "text": "<b>Ex 3D · Q1(h)</b> · By the division method, √2601 =", "opts": ["61", "51", "41", "49"], "correct": 1, "tag": "", "sol": "5<sup>2</sup> = 25 ≤ 26, remainder 1; bring down → 101; 101 × 1 = 101, remainder 0. So √2601 = 51."}, {"kind": "blank", "p": "<b>Ex 3D · Q1(i)</b> · Find the square root by the division method.", "tag": "", "marks": "", "flat": [{"t": "i) √831744 = __B1__", "a": {"B1": "912"}}], "sol": "i) 9<sup>2</sup> = 81 ≤ 83, remainder 2; bring down → 217; 181 × 1 = 181, remainder 36; bring down → 3644; 1822 × 2 = 3644, remainder 0. So √831744 = 912."}, {"kind": "blank", "p": "<b>Ex 3D · Q2(a–e)</b> · Find the square root (in lowest terms).", "tag": "", "marks": "", "flat": [{"t": "a) {4/9} → __B1__", "a": {"B1": "2/3"}, "expr": "fl"}, {"t": "b) {16/25} → __B1__", "a": {"B1": "4/5"}, "expr": "fl"}, {"t": "c) {9/16} → __B1__", "a": {"B1": "3/4"}, "expr": "fl"}, {"t": "d) {64/225} → __B1__", "a": {"B1": "8/15"}, "expr": "fl"}, {"t": "e) {81/100} → __B1__", "a": {"B1": "9/10"}, "expr": "fl"}], "sol": "{2/3}.\n{4/5}.\n{3/4}.\n{8/15}.\n{9/10}."}, {"kind": "mcq", "text": "<b>Ex 3D · Q2(f)</b> · The square root of {144/400}, in lowest terms, is", "opts": ["{3/10}", "{3/5}", "{9/25}", "{6/25}"], "correct": 1, "tag": "", "sol": "√144 = 12 and √400 = 20: {12/20} = {3/5}. ({9/25} is the fraction itself in lowest terms.)"}, {"kind": "blank", "p": "<b>Ex 3D · Q2(g–i)</b> · Find the square root.", "tag": "", "marks": "", "flat": [{"t": "g) {1024/2401} → __B1__", "a": {"B1": "32/49"}, "expr": "fl"}, {"t": "h) {3 1269/1764} → __B1__", "a": {"B1": "27/14"}, "expr": "fv"}, {"t": "i) (2 × 2 × 2 × 2)/(3 × 3 × 5 × 5) → __B1__", "a": {"B1": "4/15"}, "expr": "fl"}], "sol": "√1024 = 32, √2401 = 49: {32/49}.\n3 × 1764 + 1269 = 6561; √6561 = 81 and √1764 = 42: {81/42} = {27/14}.\n(2 × 2)/(3 × 5) = {4/15}."}, {"kind": "blank", "p": "<b>Ex 3D · Q3(a–c)</b> · Find the square root of each decimal.", "tag": "", "marks": "", "flat": [{"t": "a) √46.24 = __B1__", "a": {"B1": "6.8"}, "expr": "dec"}, {"t": "b) √82.81 = __B1__", "a": {"B1": "9.1"}, "expr": "dec"}, {"t": "c) √4637.61 = __B1__", "a": {"B1": "68.1"}, "expr": "dec"}], "sol": "6<sup>2</sup> = 36 ≤ 46, remainder 10; bring down → 1024; 128 × 8 = 1024, remainder 0. So √46.24 = 6.8.\n9<sup>2</sup> = 81 ≤ 82, remainder 1; bring down → 181; 181 × 1 = 181, remainder 0. So √82.81 = 9.1.\n6<sup>2</sup> = 36 ≤ 46, remainder 10; bring down → 1037; 128 × 8 = 1024, remainder 13; bring down → 1361; 1361 × 1 = 1361, remainder 0. So √4637.61 = 68.1."}, {"kind": "mcq", "text": "<b>Ex 3D · Q3(d)</b> · By the division method, √13.69 =", "opts": ["0.37", "3.07", "37", "3.7"], "correct": 3, "tag": "", "sol": "Pairs 13 . 69: 3<sup>2</sup> = 9, remainder 4; bring down 69 → 469; 67 × 7 = 469, remainder 0. One period before the point, so one digit before the point: 3.7. Check: 3.7 × 3.7 = 13.69."}, {"kind": "blank", "p": "<b>Ex 3D · Q3(e–g)</b> · Find the square root of each decimal.", "tag": "", "marks": "", "flat": [{"t": "e) √1772.41 = __B1__", "a": {"B1": "42.1"}, "expr": "dec"}, {"t": "f) √8136.04 = __B1__", "a": {"B1": "90.2"}, "expr": "dec"}, {"t": "g) √268.96 = __B1__", "a": {"B1": "16.4"}, "expr": "dec"}], "sol": "4<sup>2</sup> = 16 ≤ 17, remainder 1; bring down → 172; 82 × 2 = 164, remainder 8; bring down → 841; 841 × 1 = 841, remainder 0. So √1772.41 = 42.1.\n9<sup>2</sup> = 81 ≤ 81, remainder 0; bring down → 36; 180 × 0 = 0, remainder 36; bring down → 3604; 1802 × 2 = 3604, remainder 0. So √8136.04 = 90.2.\n1<sup>2</sup> = 1 ≤ 2, remainder 1; bring down → 168; 26 × 6 = 156, remainder 12; bring down → 1296; 324 × 4 = 1296, remainder 0. So √268.96 = 16.4."}, {"kind": "mcq", "text": "<b>Ex 3D · Q4(a)</b> · The square root of 70 correct up to 2 decimal places is", "opts": ["8.40", "8.36", "8.37", "8.47"], "correct": 2, "tag": "", "sol": "√70 = 8.366… by the division method (8<sup>2</sup> = 64, then 163 × 3, 1666 × 6, 16726 × 6); to 2 decimal places 8.37."}, {"kind": "blank", "p": "<b>Ex 3D · Q4(b–d)</b> · Find the square root correct up to 2 decimal places.", "tag": "", "marks": "", "flat": [{"t": "b) √89 ≈ __B1__", "a": {"B1": "9.43"}, "expr": "dec"}, {"t": "c) √134 ≈ __B1__", "a": {"B1": "11.58"}, "expr": "dec"}, {"t": "d) √526 ≈ __B1__", "a": {"B1": "22.93"}, "expr": "dec"}], "sol": "√89 = 9.433… ≈ 9.43.\n√134 = 11.575… ≈ 11.58.\n√526 = 22.934… ≈ 22.93."}]}, {"id": "s6", "label": "3.6 Estimation & uses", "sub": "Estimating square roots, nearest perfect squares and word problems", "slides": [{"kind": "blank", "p": "<b>Example 25</b> · Find the greatest 4-digit number which is a perfect square.", "tag": "", "marks": "", "flat": [{"t": "Remainder when √9999 is found by division = __B1__", "a": {"B1": "198"}}, {"t": "Greatest 4-digit perfect square = __B1__", "a": {"B1": "9801"}}], "sol": "9<sup>2</sup> = 81, remainder 18; bring down 99 → 1899; 189 × 9 = 1701, remainder 198.\n9999 − 198 = 9801 = 99<sup>2</sup>."}, {"kind": "mcq", "text": "<b>Example 26</b> · The smallest number by which 79380 must be multiplied or divided to get a perfect square is", "opts": ["7", "3", "5", "2"], "correct": 2, "tag": "", "sol": "79380 = (2 × 2) × (3 × 3) × (3 × 3) × (7 × 7) × 5. Only the 5 has no partner, so multiply or divide by 5."}, {"kind": "blank", "p": "<b>Example 27</b> · 1156 students form a square pattern for the mass drill. How many students form each side of the square?", "tag": "", "marks": "", "flat": [{"t": "Students on each side = __B1__", "a": {"B1": "34"}}], "sol": "x × x = 1156, so x = √1156: 3<sup>2</sup> = 9, remainder 2; bring down 56 → 256; 64 × 4 = 256. So 34 students."}, {"kind": "blank", "p": "<b>Example 28</b> · The perimeter of a square field is 176 m. What is the area of the field?", "tag": "", "marks": "", "flat": [{"t": "Side = __B1__ m", "a": {"B1": "44"}}, {"t": "Area = __B1__ sq. m", "a": {"B1": "1936"}}], "sol": "176 ÷ 4 = 44 m.\n44 × 44 = 1936 sq. m."}, {"kind": "mcq", "text": "<b>Example 29</b> · A cloth has area 634 cm<sup>2</sup>. Can a square table cloth of side 26 cm be made from it?", "opts": ["No, a 26 cm square needs 676 cm<sup>2</sup>, more than 634", "Yes, because 26 × 4 = 104 is less than 634", "Yes, because 634 ÷ 26 is more than 24", "No, because 634 is not a multiple of 26"], "correct": 0, "tag": "", "sol": "Area needed = 26<sup>2</sup> = 676 cm<sup>2</sup> and 676 > 634, so the table cloth cannot be made."}, {"kind": "blank", "p": "<b>Example 30</b> · A rectangular hall is 24 m long and 18 m wide. What is the length of the largest straight line that can be drawn on the floor?", "tag": "", "marks": "", "flat": [{"t": "24<sup>2</sup> + 18<sup>2</sup> = __B1__", "a": {"B1": "900"}}, {"t": "Largest line = __B1__ m", "a": {"B1": "30"}}], "sol": "576 + 324 = 900.\nThe diagonal = √900 = 30 m.", "fig": "<svg class=\"figsvg\" viewBox=\"0 0 300 160\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><rect class=\"sh3\" x=\"50\" y=\"30\" width=\"200\" height=\"100\"/><line class=\"ln hid\" x1=\"50.0\" y1=\"130.0\" x2=\"250.0\" y2=\"30.0\"/><text class=\"lb\" x=\"150.0\" y=\"147.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">24 m</text><text class=\"lb\" x=\"258.0\" y=\"80.0\" text-anchor=\"start\" dominant-baseline=\"middle\">18 m</text><text class=\"al\" x=\"138.0\" y=\"68.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">?</text></svg>"}, {"kind": "mcq", "text": "Estimate √251 to the nearest whole number.", "opts": ["15", "13", "16", "25"], "correct": 2, "tag": "", "sol": "15<sup>2</sup> = 225 and 16<sup>2</sup> = 256. 251 is closer to 256, so √251 ≈ 16."}, {"kind": "blank", "p": "<b>Example 31</b> · Find the square root of 256 by estimation.", "tag": "", "marks": "", "flat": [{"t": "Tens digit of the root = __B1__", "a": {"B1": "1"}}, {"t": "√256 = __B1__", "a": {"B1": "16"}}], "sol": "256 ends in 6 → root ends in 4 or 6. Ignore “56”: 1<sup>2</sup> = 1 ≤ 2 < 4, so the tens digit is 1.\n14 or 16; 15<sup>2</sup> = 225 < 256, so √256 = 16."}, {"kind": "mcq", "text": "<b>Example 32</b> · 3136 ends in 6 and 5<sup>2</sup> ≤ 31 < 6<sup>2</sup>. Given 55<sup>2</sup> = 3025, √3136 =", "opts": ["56", "46", "66", "54"], "correct": 0, "tag": "", "sol": "The root is 54 or 56. 3136 > 3025 = 55<sup>2</sup>, so √3136 = 56 (56 × 56 = 3136)."}, {"kind": "blank", "p": "<b>Example 33</b> · Find the square root of 3844 by estimation.", "tag": "", "marks": "", "flat": [{"t": "√3844 = __B1__", "a": {"B1": "62"}}], "sol": "Units digit 4 → root ends in 2 or 8. 6<sup>2</sup> = 36 ≤ 38 < 49, so 62 or 68. 65<sup>2</sup> = 4225 > 3844, so √3844 = 62."}, {"kind": "mcq", "text": "<b>Try This (p. 50) · Q2</b> · The area of a square field is 4096 m<sup>2</sup>. The length of each side is", "opts": ["66 m", "1024 m", "62 m", "64 m"], "correct": 3, "tag": "", "sol": "Side = √4096: 40|96, 6<sup>2</sup> = 36, remainder 4; bring down 96 → 496; 124 × 4 = 496. Side = 64 m."}, {"kind": "blank", "p": "<b>Maths and Art</b> · In a Pythagoras tree, a right isosceles triangle sits on top of a square of side 10 cm (its hypotenuse is the top edge). A square is built on each of the other two sides.", "tag": "", "marks": "", "flat": [{"t": "Area of the first square = __B1__ cm<sup>2</sup>", "a": {"B1": "100"}}, {"t": "Area of each new square = __B1__ cm<sup>2</sup>", "a": {"B1": "50"}}], "sol": "10 × 10 = 100 cm<sup>2</sup>.\nBy Pythagoras, the two equal sides satisfy s<sup>2</sup> + s<sup>2</sup> = 100, so each new square has area s<sup>2</sup> = 50 cm<sup>2</sup>."}, {"kind": "blank", "p": "<b>Ex 3D · Q5(a–c)</b> · Estimate the square root using the units digit and the hundreds/thousands pair.", "tag": "", "marks": "", "flat": [{"t": "a) √2916 = __B1__", "a": {"B1": "54"}}, {"t": "b) √3844 = __B1__", "a": {"B1": "62"}}, {"t": "c) √9025 = __B1__", "a": {"B1": "95"}}], "sol": "6 → 4 or 6; 29 → 5_; 55<sup>2</sup> = 3025 > 2916 → 54.\n4 → 2 or 8; 38 → 6_; 65<sup>2</sup> = 4225 > 3844 → 62.\nEnds in 25 → ends in 5; 90 → 9_: 95."}, {"kind": "mcq", "text": "<b>Ex 3D · Q5(d)</b> · √144 =", "opts": ["12", "14", "18", "72"], "correct": 0, "tag": "", "sol": "4 → 2 or 8; 1 → tens digit 1; so 12 or 18. 15<sup>2</sup> = 225 > 144, so 12."}, {"kind": "blank", "p": "<b>Ex 3D · Q5(e, f)</b> · Estimate the square root.", "tag": "", "marks": "", "flat": [{"t": "e) √676 = __B1__", "a": {"B1": "26"}}, {"t": "f) √4225 = __B1__", "a": {"B1": "65"}}], "sol": "6 → 4 or 6; 6 → tens digit 2; 25<sup>2</sup> = 625 < 676 → 26.\nEnds in 25 → 5; 42 → 6_: 65."}, {"kind": "mcq", "text": "<b>Ex 3D · Q6</b> · The length of each side of a square field is 63 m. Its area is", "opts": ["126 sq. m", "3869 sq. m", "3969 sq. m", "252 sq. m"], "correct": 2, "tag": "", "sol": "63 × 63 = 3969 sq. m. (252 m is the perimeter.)"}, {"kind": "blank", "p": "<b>Ex 3D · Q7</b> · A square room of side 12 m is to be paved with square tiles of side 50 cm. How many tiles are needed?", "tag": "", "marks": "", "flat": [{"t": "Tiles along one side = __B1__", "a": {"B1": "24"}}, {"t": "Number of tiles = __B1__", "a": {"B1": "576"}}], "sol": "12 m = 1200 cm; 1200 ÷ 50 = 24.\n24 × 24 = 576 tiles."}, {"kind": "mcq", "text": "<b>Ex 3D · Q8</b> · The perimeter of a square plot of land is 64 m. The area of the plot is", "opts": ["64 sq. m", "1024 sq. m", "256 sq. m", "4096 sq. m"], "correct": 2, "tag": "", "sol": "Side = 64 ÷ 4 = 16 m; area = 16<sup>2</sup> = 256 sq. m."}, {"kind": "blank", "p": "<b>Ex 3D · Q9</b> · Find the length of the hypotenuse of a right-angled triangle whose other sides are 12 m and 5 m.", "tag": "", "marks": "", "flat": [{"t": "Hypotenuse = __B1__ m", "a": {"B1": "13"}}], "sol": "12<sup>2</sup> + 5<sup>2</sup> = 144 + 25 = 169; √169 = 13 m.", "fig": "<svg class=\"figsvg\" viewBox=\"0 0 300 170\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><line class=\"ln\" x1=\"30.0\" y1=\"140.0\" x2=\"215.0\" y2=\"140.0\"/><line class=\"ln\" x1=\"215.0\" y1=\"140.0\" x2=\"215.0\" y2=\"30.0\"/><line class=\"ln\" x1=\"30.0\" y1=\"140.0\" x2=\"215.0\" y2=\"30.0\"/><path class=\"ra\" d=\"M215.0,129.0 L204.0,129.0 L204.0,140.0\"/><text class=\"lb\" x=\"122.0\" y=\"157.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">12 m</text><text class=\"lb\" x=\"222.0\" y=\"85.0\" text-anchor=\"start\" dominant-baseline=\"middle\">5 m</text><text class=\"al\" x=\"108.0\" y=\"70.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">?</text></svg>"}, {"kind": "mcq", "text": "<b>Ex 3D · Q10</b> · Sharon has cloth of area 170 cm<sup>2</sup>. Can she make a square handkerchief of side 12.5 cm?", "opts": ["Yes, it needs 156.25 cm<sup>2</sup>, which is less than 170", "No, 170 is not a perfect square", "No, it needs 172.5 cm<sup>2</sup>, which is more than 170", "Yes, because 4 × 12.5 = 50 is less than 170"], "correct": 0, "tag": "", "sol": "12.5<sup>2</sup> = 156.25 cm<sup>2</sup> < 170 cm<sup>2</sup>, so yes."}, {"kind": "blank", "p": "<b>Ex 3D · Q11</b> · Find the least number that must be subtracted from 5630 to get a perfect square. Also find the square root of that perfect square.", "tag": "", "marks": "", "flat": [{"t": "Number to subtract = __B1__", "a": {"B1": "5"}}, {"t": "Square root = __B1__", "a": {"B1": "75"}}], "sol": "√5630 by division: 7<sup>2</sup> = 49, remainder 7; bring down 30 → 730; 145 × 5 = 725, remainder 5.\n5630 − 5 = 5625 = 75<sup>2</sup>."}, {"kind": "mcq", "text": "<b>Ex 3D · Q12</b> · The smallest 6-digit number which is a perfect square is", "opts": ["100489", "100000", "100100", "101124"], "correct": 0, "tag": "", "sol": "√100000 ≈ 316.2, so 316<sup>2</sup> = 99856 (5 digits) and 317<sup>2</sup> = 100489. (101124 = 318<sup>2</sup> is bigger.)"}, {"kind": "blank", "p": "<b>HOTS · Q1</b> · The area of a square field is 4096 m<sup>2</sup>. What is the length of each side?", "tag": "", "marks": "", "flat": [{"t": "Side = __B1__ m", "a": {"B1": "64"}}], "sol": "√4096 = 64 (64 × 64 = 4096)."}]}, {"id": "s7", "label": "Assessment A", "sub": "Knowing and understanding", "slides": [{"kind": "mcq", "text": "<b>Check-up · MCQ 1</b> · Which of the following is not a perfect square?", "opts": ["441", "1225", "676", "1083"], "correct": 3, "tag": "", "sol": "441 = 21<sup>2</sup>, 1225 = 35<sup>2</sup>, 676 = 26<sup>2</sup>. 1083 ends in 3, and no square ends in 3."}, {"kind": "mcq", "text": "<b>Check-up · MCQ 2</b> · A perfect square can never have ____ at ones place.", "opts": ["7", "4", "9", "6"], "correct": 0, "tag": "", "sol": "Squares end only in 0, 1, 4, 5, 6 or 9, so never in 7."}, {"kind": "blank", "p": "<b>Check-up · Q3</b> · Find the square root of each expression.", "tag": "", "marks": "", "flat": [{"t": "a) 3 × 3 × 4 × 4 → __B1__", "a": {"B1": "12"}}, {"t": "b) 324 → __B1__", "a": {"B1": "18"}}, {"t": "c) {9/64} → __B1__", "a": {"B1": "3/8"}, "expr": "fl"}], "sol": "3 × 4 = 12.\n324 = (2 × 2)(3 × 3)(3 × 3): 2 × 3 × 3 = 18.\n{3/8}."}, {"kind": "mcq", "text": "<b>Check-up · Q5(a)</b> · The simplest answer for √(m<sup>12</sup>) is", "opts": ["m<sup>10</sup>", "m<sup>24</sup>", "m<sup>6</sup>", "6m"], "correct": 2, "tag": "", "sol": "m<sup>12</sup> = m<sup>6</sup> × m<sup>6</sup>, so √(m<sup>12</sup>) = m<sup>6</sup> (halve the exponent)."}, {"kind": "blank", "p": "<b>Check-up · Q6</b> · Find the squares of the following numbers.", "tag": "", "marks": "", "flat": [{"t": "a) {6/7} → __B1__", "a": {"B1": "36/49"}, "expr": "fl"}, {"t": "b) {10/11} → __B1__", "a": {"B1": "100/121"}, "expr": "fl"}, {"t": "c) (−9)<sup>2</sup> = __B1__", "a": {"B1": "81"}}, {"t": "d) (−7)<sup>2</sup> = __B1__", "a": {"B1": "49"}}], "sol": "{36/49}.\n{100/121}.\n(−9) × (−9) = 81.\n(−7) × (−7) = 49."}, {"kind": "mcq", "text": "<b>Check-up · Q5(b)</b> · The simplest answer for √(16x<sup>4</sup>y<sup>8</sup>) is", "opts": ["4x<sup>2</sup>y<sup>4</sup>", "4x<sup>4</sup>y<sup>8</sup>", "16x<sup>2</sup>y<sup>4</sup>", "8x<sup>2</sup>y<sup>4</sup>"], "correct": 0, "tag": "", "sol": "√16 = 4, √(x<sup>4</sup>) = x<sup>2</sup>, √(y<sup>8</sup>) = y<sup>4</sup>: 4x<sup>2</sup>y<sup>4</sup>."}, {"kind": "blank", "p": "<b>Check-up · Q9</b> · Find the values.", "tag": "", "marks": "", "flat": [{"t": "a) 46<sup>2</sup> = __B1__", "a": {"B1": "2116"}}, {"t": "b) 45<sup>2</sup> = __B1__", "a": {"B1": "2025"}}, {"t": "c) 85<sup>2</sup> = __B1__", "a": {"B1": "7225"}}], "sol": "46 × 46 = 2116.\n4 × 5 = 20 → 2025.\n8 × 9 = 72 → 7225."}, {"kind": "mcq", "text": "<b>Mental Maths (p. 54) · Q1</b> · What is the square of (−abc)?", "opts": ["a<sup>2</sup>b<sup>2</sup>c<sup>2</sup>", "−a<sup>2</sup>b<sup>2</sup>c<sup>2</sup>", "(abc)<sup>−2</sup>", "−2abc"], "correct": 0, "tag": "", "sol": "(−abc) × (−abc) = (+)a<sup>2</sup>b<sup>2</sup>c<sup>2</sup>: a square is never negative."}, {"kind": "blank", "p": "<b>Mental Maths (p. 54) · Q4</b> · Fill in the blanks.", "tag": "", "marks": "", "flat": [{"t": "a) If 13 × 13 = 169, then √169 = __B1__", "a": {"B1": "13"}}, {"t": "b) If 5 × 5 = 25, then √25 = __B1__", "a": {"B1": "5"}}, {"t": "c) If 8 × 8 = 64, then √64 = __B1__", "a": {"B1": "8"}}, {"t": "d) If 16 × 16 = 256, then √256 = __B1__", "a": {"B1": "16"}}, {"t": "e) If 3<sup>2</sup> = 9, then √9 = __B1__", "a": {"B1": "3"}}, {"t": "f) If (3 × 7) × (3 × 7) = 441, then √441 = __B1__", "a": {"B1": "21"}}, {"t": "g) If (3 × 3 × 7)<sup>2</sup> = 3969, then √3969 = __B1__", "a": {"B1": "63"}}], "sol": "13.\n5.\n8.\n16.\n3.\n3 × 7 = 21.\n3 × 3 × 7 = 63."}]}, {"id": "s8", "label": "Assessment B", "sub": "Investigating patterns", "slides": [{"kind": "blank", "p": "<b>Check-up · Q4(a)</b> · Find the smallest whole number that must be added to 575 to make it a perfect square. Also find the square root of the new number.", "tag": "", "marks": "", "flat": [{"t": "Number to add = __B1__", "a": {"B1": "1"}}, {"t": "Square root = __B1__", "a": {"B1": "24"}}], "sol": "23<sup>2</sup> = 529 < 575 < 576 = 24<sup>2</sup>.\n575 + 1 = 576, √576 = 24."}, {"kind": "mcq", "text": "<b>Check-up · Q4(b)</b> · Find the smallest whole number that must be added to 1700 to make it a perfect square, and the square root of the new number.", "opts": ["36; √1736 = 42", "19; √1719 = 41", "64; √1764 = 42", "81; √1781 = 42"], "correct": 2, "tag": "", "sol": "41<sup>2</sup> = 1681 < 1700 < 1764 = 42<sup>2</sup>. 1764 − 1700 = 64, and the new number has square root 42. (19 would have to be subtracted, not added.)"}, {"kind": "blank", "p": "<b>Check-up · Q4(c)</b> · Find the smallest whole number that must be added to 250 to make it a perfect square, and the square root of the new number.", "tag": "", "marks": "", "flat": [{"t": "Number to add = __B1__", "a": {"B1": "6"}}, {"t": "Square root = __B1__", "a": {"B1": "16"}}], "sol": "15<sup>2</sup> = 225 < 250 < 256 = 16<sup>2</sup>; 256 − 250 = 6.\n√256 = 16."}, {"kind": "mcq", "text": "<b>Mental Maths (p. 54) · Q2</b> · In the square of any number with 5 as its units digit, the tens and units digits are", "opts": ["tens 0, units 5", "tens 5, units 5", "tens 2, units 5", "tens 5, units 2"], "correct": 2, "tag": "", "sol": "5 × 5 = 25 is always written at the end (e.g. 35<sup>2</sup> = 1225, 75<sup>2</sup> = 5625), so the tens digit is 2 and the units digit is 5."}, {"kind": "blank", "p": "<b>Check-up · Q10</b> · Estimate the square root of each number.", "tag": "", "marks": "", "flat": [{"t": "a) √6241 = __B1__", "a": {"B1": "79"}}, {"t": "b) √1849 = __B1__", "a": {"B1": "43"}}, {"t": "c) √2209 = __B1__", "a": {"B1": "47"}}], "sol": "1 → 1 or 9; 62 → 7_ (49 ≤ 62 < 64); 75<sup>2</sup> = 5625 < 6241 → 79.\n9 → 3 or 7; 18 → 4_; 45<sup>2</sup> = 2025 > 1849 → 43.\n9 → 3 or 7; 22 → 4_; 45<sup>2</sup> = 2025 < 2209 → 47."}, {"kind": "mcq", "text": "<b>Mental Maths (p. 54) · Q3</b> · The square root of 2 × 2 × 3 × 3 × 3 × 3 × 5 × 5 is", "opts": ["30", "180", "90", "45"], "correct": 2, "tag": "", "sol": "Pairs: (2 × 2)(3 × 3)(3 × 3)(5 × 5); one from each: 2 × 3 × 3 × 5 = 90."}, {"kind": "blank", "p": "A square leaves remainder 0 or 1 when divided by 3 or by 4. Check with 7<sup>2</sup> = 49 and 6<sup>2</sup> = 36.", "tag": "", "marks": "", "flat": [{"t": "Remainder of 49 ÷ 3 = __B1__", "a": {"B1": "1"}}, {"t": "Remainder of 49 ÷ 4 = __B1__", "a": {"B1": "1"}}, {"t": "Remainder of 36 ÷ 4 = __B1__", "a": {"B1": "0"}}], "sol": "49 = 3 × 16 + 1.\n49 = 4 × 12 + 1.\n36 = 4 × 9 + 0."}, {"kind": "mcq", "text": "Using the remainder pattern, which number cannot be a perfect square even though its units digit is 1?", "opts": ["961", "841", "1681", "1001"], "correct": 3, "tag": "", "sol": "1001 = 3 × 333 + 2 leaves remainder 2 on division by 3, so it is not a square. 961 = 31<sup>2</sup>, 841 = 29<sup>2</sup>, 1681 = 41<sup>2</sup>."}, {"kind": "blank", "p": "The square of an odd number is the sum of two consecutive numbers: 3<sup>2</sup> = 4 + 5, 5<sup>2</sup> = 12 + 13, 7<sup>2</sup> = 24 + 25. Continue for 11<sup>2</sup>.", "tag": "", "marks": "", "flat": [{"t": "11<sup>2</sup> = __B1__ + __B2__", "a": {"B1": "60", "B2": "61"}}], "sol": "11<sup>2</sup> = 121 = 60 + 61 (the smaller number is (121 − 1) ÷ 2 = 60)."}, {"kind": "blank", "p": "<b>HOTS · Q3</b> · Find the square root of 1,86,62,400.", "tag": "", "marks": "", "flat": [{"t": "√18662400 = __B1__", "a": {"B1": "4320"}}], "sol": "18662400 = 186624 × 100; √186624 = 432 (division method) and √100 = 10, so the root is 4320."}]}, {"id": "s9", "label": "Assessment C", "sub": "Communicating", "slides": [{"kind": "blank", "p": "<b>Check-up · Q7</b> · Find the square roots by the division method.", "tag": "", "marks": "", "flat": [{"t": "a) √289 = __B1__", "a": {"B1": "17"}}, {"t": "b) √26244 = __B1__", "a": {"B1": "162"}}, {"t": "c) √361201 = __B1__", "a": {"B1": "601"}}], "sol": "1<sup>2</sup> = 1 ≤ 2, remainder 1; bring down → 189; 27 × 7 = 189, remainder 0. So √289 = 17.\n1<sup>2</sup> = 1 ≤ 2, remainder 1; bring down → 162; 26 × 6 = 156, remainder 6; bring down → 644; 322 × 2 = 644, remainder 0. So √26244 = 162.\n6<sup>2</sup> = 36 ≤ 36, remainder 0; bring down → 12; 120 × 0 = 0, remainder 12; bring down → 1201; 1201 × 1 = 1201, remainder 0. So √361201 = 601."}, {"kind": "mcq", "text": "Sonu writes −4<sup>2</sup> = 16. Which reply is correct?", "opts": ["Yes: squaring always makes a number positive", "No: −4<sup>2</sup> = −(4 × 4) = −16; only (−4)<sup>2</sup> = 16", "No: −4<sup>2</sup> = −8, because the square doubles the number", "No: −4<sup>2</sup> = 8, because two negatives make a positive"], "correct": 1, "tag": "", "sol": "Without brackets only the 4 is squared. The square of −4 must be written (−4)<sup>2</sup> = 16."}, {"kind": "blank", "p": "<b>Check-up · Q8</b> · Find the square roots of the decimals.", "tag": "", "marks": "", "flat": [{"t": "a) √6.76 = __B1__", "a": {"B1": "2.6"}, "expr": "dec"}, {"t": "b) √32.49 = __B1__", "a": {"B1": "5.7"}, "expr": "dec"}], "sol": "2<sup>2</sup> = 4 ≤ 6, remainder 2; bring down → 276; 46 × 6 = 276, remainder 0. So √6.76 = 2.6.\n5<sup>2</sup> = 25 ≤ 32, remainder 7; bring down → 749; 107 × 7 = 749, remainder 0. So √32.49 = 5.7."}, {"kind": "mcq", "text": "Which statement about 81,000 is correct?", "opts": ["It is not a perfect square, because it ends in an odd number of zeros", "It is a perfect square, because 81 is a perfect square", "It is not a perfect square, because it is even", "It is a perfect square, because it ends in 0"], "correct": 0, "tag": "", "sol": "81,000 = 9<sup>2</sup> × 10<sup>2</sup> × 10: the last 10 has no partner (Property 3)."}, {"kind": "blank", "p": "<b>HOTS · Q4</b> · Find the square root of 641.8464 up to 3 decimal places.", "tag": "", "marks": "", "flat": [{"t": "√641.8464 ≈ __B1__", "a": {"B1": "25.335"}, "expr": "dec"}], "sol": "Periods 6 41 . 84 64 (00): the division method gives 25.3346…, which is 25.335 to 3 decimal places."}, {"kind": "mcq", "text": "How many digits does the square root of 18662400 have?", "opts": ["5", "3", "4", "8"], "correct": 2, "tag": "", "sol": "Bars from the units digit: 18|66|24|00 → 4 bars, so 4 digits (4320)."}, {"kind": "blank", "p": "Complete the statements.", "tag": "", "marks": "", "flat": [{"t": "The square of an odd number is __B1__.", "a": {"B1": "odd"}, "expr": "words"}, {"t": "A number ending in 2, 3, 7 or 8 is never a perfect __B1__.", "a": {"B1": "square"}, "expr": "words", "accept": ["squarenumber"]}, {"t": "There are __B1__ whole numbers between 20<sup>2</sup> and 21<sup>2</sup>.", "a": {"B1": "40"}}], "sol": "Property 4.\nProperty 1.\nProperty 7: 2 × 20 = 40."}, {"kind": "mcq", "text": "Riya says “√{9/16} = {9/4}, because you take the root of the denominator only.” Which reply is correct?", "opts": ["No: take the root of both, √9 ÷ √16 = {3/4}", "No: halve both parts, 4.5 ÷ 8", "Yes: only the denominator needs a root", "No: take the root of the numerator only, {3/16}"], "correct": 0, "tag": "", "sol": "√({a/b}) = √a / √b, so √({9/16}) = {3/4}. Check: {3/4} × {3/4} = {9/16}."}, {"kind": "mcq", "text": "<b>Being Indian (b)</b> · The society is organising a function on World Senior Citizen’s Day. How can you show your respect for the elders?", "opts": ["Help them, listen to them and spend time with them all year", "Give them a gift at the function and then leave early", "Greet them politely only on special days like this one", "Arrange the seats for them but leave the talking to the adults"], "correct": 0, "tag": "", "sol": "Respect is shown every day by helping elders, listening to them, spending time with them and caring for their needs."}]}, {"id": "s10", "label": "Assessment D", "sub": "Applying mathematics in real-life contexts", "slides": [{"kind": "blank", "p": "<b>Check-up · Q11</b> · Two buildings are 20 m and 25 m high and 12 m apart. Find the distance between their tops.", "tag": "", "marks": "", "flat": [{"t": "Difference in heights = __B1__ m", "a": {"B1": "5"}}, {"t": "Distance between the tops = __B1__ m", "a": {"B1": "13"}}], "sol": "25 − 20 = 5 m.\n5<sup>2</sup> + 12<sup>2</sup> = 25 + 144 = 169; √169 = 13 m.", "fig": "<svg class=\"figsvg\" viewBox=\"0 0 300 180\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><rect class=\"sh3\" x=\"60\" y=\"64.0\" width=\"30\" height=\"96.0\"/><rect class=\"sh3\" x=\"200\" y=\"40.0\" width=\"30\" height=\"120.0\"/><line class=\"ln\" x1=\"10.0\" y1=\"160.0\" x2=\"290.0\" y2=\"160.0\"/><line class=\"arm\" x1=\"90.0\" y1=\"64.0\" x2=\"200.0\" y2=\"40.0\"/><line class=\"ln hid\" x1=\"90.0\" y1=\"64.0\" x2=\"200.0\" y2=\"64.0\"/><text class=\"lb\" x=\"55.0\" y=\"112.0\" text-anchor=\"end\" dominant-baseline=\"middle\">20 m</text><text class=\"lb\" x=\"235.0\" y=\"100.0\" text-anchor=\"start\" dominant-baseline=\"middle\">25 m</text><text class=\"lb\" x=\"145.0\" y=\"173.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">12 m</text><text class=\"al\" x=\"145.0\" y=\"40.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">?</text></svg>"}, {"kind": "mcq", "text": "<b>Check-up · Q12</b> · The area of a town in the form of a square is 729 sq. km. The length of each side is", "opts": ["27.9 km", "29 km", "182.25 km", "27 km"], "correct": 3, "tag": "", "sol": "729 = 3<sup>6</sup>, so √729 = 3<sup>3</sup> = 27 km. (182.25 = 729 ÷ 4.)"}, {"kind": "blank", "p": "<b>Check-up · Case study Q13(a)</b> · Raghav’s city has an area of 504.9009 sq. km. If the city is a square, find the length of each side of its border.", "tag": "", "marks": "", "flat": [{"t": "Side = __B1__ km", "a": {"B1": "22.47"}, "expr": "dec"}], "sol": "2<sup>2</sup> = 4 ≤ 5, remainder 1; bring down → 104; 42 × 2 = 84, remainder 20; bring down → 2090; 444 × 4 = 1776, remainder 314; bring down → 31409; 4487 × 7 = 31409, remainder 0. So √504.9009 = 22.47. km."}, {"kind": "mcq", "text": "<b>Check-up · Case study Q13(b)</b> · Raghav’s building is 60 m high; another building is 50 m high, 24 m away. The distance between their tops is", "opts": ["34 m", "25 m", "110 m", "26 m"], "correct": 3, "tag": "", "sol": "Difference in heights = 10 m. 10<sup>2</sup> + 24<sup>2</sup> = 100 + 576 = 676, and √676 = 26 m.", "fig": "<svg class=\"figsvg\" viewBox=\"0 0 300 180\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><rect class=\"sh3\" x=\"60\" y=\"40.0\" width=\"30\" height=\"120.0\"/><rect class=\"sh3\" x=\"200\" y=\"60.0\" width=\"30\" height=\"100.0\"/><line class=\"ln\" x1=\"10.0\" y1=\"160.0\" x2=\"290.0\" y2=\"160.0\"/><line class=\"arm\" x1=\"90.0\" y1=\"40.0\" x2=\"200.0\" y2=\"60.0\"/><line class=\"ln hid\" x1=\"90.0\" y1=\"60.0\" x2=\"200.0\" y2=\"60.0\"/><text class=\"lb\" x=\"55.0\" y=\"100.0\" text-anchor=\"end\" dominant-baseline=\"middle\">60 m</text><text class=\"lb\" x=\"235.0\" y=\"110.0\" text-anchor=\"start\" dominant-baseline=\"middle\">50 m</text><text class=\"lb\" x=\"145.0\" y=\"173.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">24 m</text><text class=\"al\" x=\"145.0\" y=\"38.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">?</text></svg>"}, {"kind": "blank", "p": "<b>Check-up · Case study Q13(c)</b> · 336 m of wire was used to fence the four sides of a square-shaped residential society. What is the area of the society?", "tag": "", "marks": "", "flat": [{"t": "Side = __B1__ m", "a": {"B1": "84"}}, {"t": "Area = __B1__ sq. m", "a": {"B1": "7056"}}], "sol": "336 ÷ 4 = 84 m.\n84 × 84 = 7056 sq. m."}, {"kind": "mcq", "text": "<b>Check-up · Everyday Maths Q14</b> · A kite is 40 m high, just above a tree. The string is 50 m long. How far is the boy from the tree?", "opts": ["30 m", "45 m", "64 m", "10 m"], "correct": 0, "tag": "", "sol": "The string is the hypotenuse: 50<sup>2</sup> − 40<sup>2</sup> = 2500 − 1600 = 900, and √900 = 30 m.", "fig": "<svg class=\"figsvg\" viewBox=\"0 0 300 170\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><line class=\"ln\" x1=\"30.0\" y1=\"140.0\" x2=\"215.0\" y2=\"140.0\"/><line class=\"ln\" x1=\"215.0\" y1=\"140.0\" x2=\"215.0\" y2=\"30.0\"/><line class=\"ln\" x1=\"30.0\" y1=\"140.0\" x2=\"215.0\" y2=\"30.0\"/><path class=\"ra\" d=\"M215.0,129.0 L204.0,129.0 L204.0,140.0\"/><text class=\"lb\" x=\"122.0\" y=\"157.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">?</text><text class=\"lb\" x=\"222.0\" y=\"85.0\" text-anchor=\"start\" dominant-baseline=\"middle\">40 m</text><text class=\"al\" x=\"108.0\" y=\"70.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">string 50 m</text><text class=\"lb\" x=\"18.0\" y=\"144.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">Boy</text><text class=\"lb\" x=\"225.0\" y=\"150.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">Tree</text><text class=\"lb\" x=\"225.0\" y=\"24.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">Kite</text></svg>"}, {"kind": "blank", "p": "<b>Check-up · Everyday Maths Q15</b> · Nita walks 160 m north and then 630 m west to a friend’s house. On the way back she walks diagonally to her house. What distance does she walk back?", "tag": "", "marks": "", "flat": [{"t": "160<sup>2</sup> + 630<sup>2</sup> = __B1__", "a": {"B1": "422500"}}, {"t": "Distance back = __B1__ m", "a": {"B1": "650"}}], "sol": "25600 + 396900 = 422500.\n√422500 = 650 m.", "fig": "<svg class=\"figsvg\" viewBox=\"0 0 300 175\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><line class=\"ln\" x1=\"215.0\" y1=\"140.0\" x2=\"215.0\" y2=\"35.0\" marker-end=\"url(#ah)\"/><line class=\"ln\" x1=\"215.0\" y1=\"35.0\" x2=\"70.0\" y2=\"35.0\" marker-end=\"url(#ah)\"/><line class=\"ln hid\" x1=\"70.0\" y1=\"35.0\" x2=\"215.0\" y2=\"140.0\"/><path class=\"ra\" d=\"M204.0,35.0 L204.0,46.0 L215.0,46.0\"/><text class=\"lb\" x=\"142.0\" y=\"22.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">630 m west</text><text class=\"lb\" x=\"222.0\" y=\"88.0\" text-anchor=\"start\" dominant-baseline=\"middle\">160 m north</text><text class=\"al\" x=\"128.0\" y=\"102.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">?</text><text class=\"lb\" x=\"215.0\" y=\"157.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">House</text><text class=\"lb\" x=\"64.0\" y=\"50.0\" text-anchor=\"end\" dominant-baseline=\"middle\">Friend</text></svg>"}, {"kind": "mcq", "text": "<b>Check-up · Everyday Maths Q16</b> · Raju’s square living room has side 3.5 m. How many square metres of carpet are needed?", "opts": ["12.25", "7", "9.25", "14"], "correct": 0, "tag": "", "sol": "Area = 3.5 × 3.5 = 12.25 m<sup>2</sup>. (14 is the perimeter in metres.)"}, {"kind": "blank", "p": "<b>Being Indian</b> · A community hall has 2704 seats. The number of rows equals the number of seats in each row. Find the number of seats in each row.", "tag": "", "marks": "", "flat": [{"t": "Seats in each row = __B1__", "a": {"B1": "52"}}], "sol": "√2704: 5<sup>2</sup> = 25 ≤ 27, remainder 2; bring down 04 → 204; 102 × 2 = 204. So 52 seats in each row."}, {"kind": "blank", "p": "<b>HOTS · Q2</b> · A square hall has side 15 m. Square tiles of side {1/2} m are used to pave it. Tiles come in boxes of 100.", "tag": "", "marks": "", "flat": [{"t": "Tiles along one side = __B1__", "a": {"B1": "30"}}, {"t": "Number of tiles = __B1__", "a": {"B1": "900"}}, {"t": "Boxes to buy = __B1__", "a": {"B1": "9"}}], "sol": "15 ÷ {1/2} = 30.\n30 × 30 = 900 tiles.\n900 ÷ 100 = 9 boxes."}]}];
/* ================= build slide lists ================= */
var SLIDES = {}; SECTIONS.forEach(function(sec){ SLIDES[sec.id]=sec.slides; });
var TAB_DEFS = SECTIONS.map(function(sec){ return {id:sec.id, label:sec.label, sub:sec.sub}; });

/* ================= state ================= */
function blankItem(slide){
  if(slide.kind==='mcq'||slide.kind==='ar'){
    return {status:'unanswered', attempts:0, choice:undefined};
  }
  return {status:'unanswered', curStep:0, stepStates: slide.flat.map(function(){ return {status:'unanswered', attempts:0, inputs:{}}; })};
}
function defaultState(){
  var s={tabs:{}};
  TAB_DEFS.forEach(function(td){
    s.tabs[td.id] = { idx:0, maxReached:0, items: SLIDES[td.id].map(function(sl){ return blankItem(sl); }) };
  });
  return s;
}
var appState = {mode:null, learning:null, quiz:null};
var state = null;      // alias for appState[appState.mode]
var MODE = null;
var activeTab=TAB_DEFS[0].id;

function setMode(m){
  appState.mode = m;
  if(!appState[m]) appState[m] = defaultState();
  state = appState[m];
  MODE = m;
}
/* ================= student accounts (saved on this device) ================= */
var SHEET_KEY='sopaan-c8-ch3';
var ACC_KEY='sopaan-students-v1';
var storageOK=true;
var MEM={};
function lsGet(k){ var r=null; try{ r=localStorage.getItem(k); }catch(e){ storageOK=false; }
  if(r===null||r===undefined) r=MEM[k]||null; try{ return r?JSON.parse(r):null; }catch(e){ return null; } }
function lsSet(k,v){ var j=JSON.stringify(v); MEM[k]=j; try{ localStorage.setItem(k,j); return true; }catch(e){ storageOK=false; return false; } }
try{ localStorage.setItem('sopaan-probe','1'); localStorage.removeItem('sopaan-probe'); }catch(e){ storageOK=false; }
function hashPin(pin,salt){ var h=2166136261, str=salt+'|'+pin; for(var i=0;i<str.length;i++){ h^=str.charCodeAt(i); h=Math.imul(h,16777619)>>>0; } return h.toString(36); }
function accKey(name,roll){ return (name.trim().toLowerCase().replace(/\s+/g,' ')+'#'+roll.trim().toLowerCase()); }
function accounts(){ return lsGet(ACC_KEY)||{students:{}}; }
var student=null; // {key,name,roll}
var records=[];   // finished-tab history for this student on this sheet
function progKey(){ return SHEET_KEY+'::'+student.key; }

function loadState(){
  appState = {mode:null, learning:null, quiz:null}; records=[]; activeTab=TAB_DEFS[0].id;
  var saved=lsGet(progKey());
  if(!saved) return;
  try{
    ['learning','quiz'].forEach(function(m){
      if(saved[m] && saved[m].tabs){
        var fresh = defaultState();
        TAB_DEFS.forEach(function(td){
          if(saved[m].tabs[td.id] && saved[m].tabs[td.id].items && saved[m].tabs[td.id].items.length===SLIDES[td.id].length){
            fresh.tabs[td.id] = saved[m].tabs[td.id];
          }
        });
        appState[m] = fresh;
      }
    });
    if(saved.mode==='learning' || saved.mode==='quiz') appState.mode = saved.mode;
    if(saved.activeTab && TAB_DEFS.some(function(t){ return t.id===saved.activeTab; })) activeTab = saved.activeTab;
    if(Array.isArray(saved.records)) records = saved.records;
  }catch(e){}
}
function saveState(){
  if(!student) return;
  lsSet(progKey(), {mode:appState.mode, learning:appState.learning, quiz:appState.quiz, activeTab:activeTab, records:records, updated:Date.now()});
  var acc=accounts(); if(acc.students[student.key]){ acc.students[student.key].last=Date.now(); lsSet(ACC_KEY,acc); }
}
function addRecord(mode, tabId, correct, revealed, skipped, total){
  records.unshift({at:Date.now(), mode:mode, tab:tabId, correct:correct, revealed:revealed, skipped:skipped, total:total});
  if(records.length>60) records.length=60;
  saveState();
}
function fmtDate(ms){ try{ return new Date(ms).toLocaleString(undefined,{day:'numeric',month:'short',hour:'2-digit',minute:'2-digit'}); }catch(e){ return ''; } }

function renderWho(){
  var el=document.getElementById('whoBar');
  if(!student){ el.hidden=true; el.innerHTML=''; return; }
  el.hidden=false;
  el.innerHTML='Signed in as <b>'+esc(student.name)+'</b> · Roll '+esc(student.roll)+
    ' <button id="btnRecord">My record</button> <button id="btnSignOut">Sign out</button>';
  document.getElementById('btnRecord').addEventListener('click', renderRecord);
  document.getElementById('btnSignOut').addEventListener('click', signOut);
}
function signOut(){
  saveState(); student=null; state=null; MODE=null;
  var acc=accounts(); delete acc.current; lsSet(ACC_KEY,acc);
  document.getElementById('modePill').hidden=true;
  renderWho(); renderLogin();
}
function signIn(key){
  var acc=accounts(); var st=acc.students[key]; if(!st) return;
  student={key:key, name:st.name, roll:st.roll};
  acc.current=key; st.last=Date.now(); lsSet(ACC_KEY,acc);
  loadState(); renderWho();
  if(appState.mode==='learning' || appState.mode==='quiz'){
    setMode(appState.mode); document.getElementById('modePill').hidden=false; updateModePill();
    showChrome(true); buildTabbar(); renderSlide();
    showToast('Welcome back, '+st.name.split(' ')[0]+'. Picking up where you left off.');
  } else {
    renderModePicker();
  }
}
function renderLogin(msg){
  showChrome(false);
  var acc=accounts(); var keys=Object.keys(acc.students).sort(function(a,b){ return (acc.students[b].last||0)-(acc.students[a].last||0); });
  var h='<div class="login-card"><h2>Student sign-in</h2>'+
    '<p class="lead">Sign in to save your answers, see your record and continue where you left off next time.</p>';
  if(!storageOK) h+='<div class="login-err">This browser is blocking saved data (for example, a private window). You can still practise, but progress will not be kept after you close the page.</div>';
  if(msg) h+='<div class="login-err">'+esc(msg)+'</div>';
  if(keys.length){
    h+='<div class="known"><span class="known-label">Continue as</span>';
    keys.slice(0,6).forEach(function(k){ var st=acc.students[k];
      h+='<button class="known-btn" data-k="'+esc(k)+'"><span>'+esc(st.name)+' <small>· Roll '+esc(st.roll)+'</small></span><small>'+(st.last?'Last active '+fmtDate(st.last):'')+'</small></button>'; });
    h+='</div>';
  }
  h+='<form id="loginForm" novalidate>'+
    '<div class="fld"><label for="lgName">Full name</label><input id="lgName" autocomplete="name" required></div>'+
    '<div class="fld-row"><div class="fld"><label for="lgRoll">Roll no.</label><input id="lgRoll" required></div>'+
    '<div class="fld"><label for="lgPin">4-digit PIN</label><input id="lgPin" type="password" inputmode="numeric" maxlength="4" autocomplete="off" required></div></div>'+
    '<button class="btn btn-primary" type="submit" style="width:100%;">Sign in</button>'+
    '<p class="login-note">New here? Enter your name, roll no. and a PIN you will remember, and your profile is created. Progress is saved on this device, so use the same device and browser to continue.</p>'+
    '</form></div>';
  var wrap=document.getElementById('wrap'); wrap.innerHTML=h;
  wrap.querySelectorAll('.known-btn').forEach(function(b){
    b.addEventListener('click', function(){
      var st=accounts().students[b.dataset.k];
      document.getElementById('lgName').value=st.name; document.getElementById('lgRoll').value=st.roll;
      document.getElementById('lgPin').focus();
    });
  });
  document.getElementById('loginForm').addEventListener('submit', function(e){
    e.preventDefault();
    var name=document.getElementById('lgName').value.trim(), roll=document.getElementById('lgRoll').value.trim(), pin=document.getElementById('lgPin').value.trim();
    if(!name||!roll){ renderLoginErr('Enter your name and roll no.'); return; }
    if(!/^\d{4}$/.test(pin)){ renderLoginErr('Your PIN must be exactly 4 digits.'); return; }
    var k=accKey(name,roll); var acc=accounts();
    if(acc.students[k]){
      if(acc.students[k].pin!==hashPin(pin,k)){ renderLoginErr('That PIN does not match this name and roll no. Try again.'); return; }
    } else {
      acc.students[k]={name:name.replace(/\s+/g,' '), roll:roll, pin:hashPin(pin,k), created:Date.now()};
      lsSet(ACC_KEY,acc);
    }
    signIn(k);
  });
}
function renderLoginErr(m){
  var n=document.getElementById('lgName').value, r=document.getElementById('lgRoll').value;
  renderLogin(m); document.getElementById('lgName').value=n; document.getElementById('lgRoll').value=r; document.getElementById('lgPin').focus();
}
function tabSummary(m){
  var st=appState[m]; if(!st) return null;
  return TAB_DEFS.map(function(td){
    var items=st.tabs[td.id].items, n=items.length;
    var c=items.filter(function(i){return i.status==='correct';}).length;
    var done=items.filter(function(i){return i.status!=='unanswered';}).length;
    return {label:td.label, n:n, done:done, correct:c};
  });
}
function renderRecord(){
  showChrome(false);
  var tabLabel=function(id){ var t=TAB_DEFS.find(function(x){return x.id===id;}); return t?t.label:id; };
  var h='<div class="rec-card"><h2>'+esc(student.name)+'’s record</h2><p class="rec-empty" style="margin:0 0 12px;">Roll '+esc(student.roll)+' · Squares and Square Roots</p>';
  ['learning','quiz'].forEach(function(m){
    var sum=tabSummary(m);
    h+='<h3>'+(m==='learning'?'📘 Learning Sheet':'📝 Quiz Mode')+'</h3>';
    if(!sum){ h+='<p class="rec-empty">Not started yet.</p>'; return; }
    h+='<div class="rec-table-wrap"><table class="rec-table"><thead><tr><th>Section</th><th>Progress</th><th>Correct first time</th></tr></thead><tbody>';
    sum.forEach(function(r){ var pct=Math.round(r.done/r.n*100);
      h+='<tr><td>'+r.label+'</td><td><span class="rec-bar"><i style="width:'+pct+'%"></i></span>'+r.done+' / '+r.n+'</td><td>'+(m==='quiz'?'—':r.correct+' / '+r.n)+'</td></tr>'; });
    h+='</tbody></table></div>';
  });
  h+='</div><div class="rec-card"><h3>Finished sections</h3>';
  if(!records.length){ h+='<p class="rec-empty">No sections finished yet. Each time you finish a tab, your score is recorded here.</p>'; }
  else {
    h+='<div class="rec-table-wrap"><table class="rec-table"><thead><tr><th>When</th><th>Mode</th><th>Section</th><th>Score</th></tr></thead><tbody>';
    records.forEach(function(r){ h+='<tr><td>'+fmtDate(r.at)+'</td><td>'+(r.mode==='quiz'?'Quiz':'Learning')+'</td><td>'+tabLabel(r.tab)+'</td><td>'+r.correct+' / '+r.total+(r.mode==='learning'?' <span class="rec-empty">('+r.revealed+' revealed, '+r.skipped+' skipped)</span>':'')+'</td></tr>'; });
    h+='</tbody></table></div>';
  }
  h+='</div><button class="btn btn-primary" id="btnBack">'+(MODE?'Back to practice':'Choose a mode')+'</button>';
  document.getElementById('wrap').innerHTML=h;
  document.getElementById('btnBack').addEventListener('click', function(){
    if(MODE){ showChrome(true); buildTabbar(); renderSlide(); } else renderModePicker();
  });
  window.scrollTo({top:0});
}

/* ================= tab bar ================= */
function buildTabbar(){
  var el=document.getElementById('tabbar');
  el.innerHTML = '<button class="tab-btn'+(activeTab==='theory'?' active':'')+'" data-tab="theory">Theory<span class="tab-count">notes</span></button>' + TAB_DEFS.map(function(t){
    return '<button class="tab-btn'+(t.id===activeTab?' active':'')+'" data-tab="'+t.id+'">'+t.label+'<span class="tab-count">'+SLIDES[t.id].length+'</span></button>';
  }).join('') + '<button class="tab-btn'+(activeTab==='report'?' active':'')+'" data-tab="report">📊 Report<span class="tab-count">pie</span></button>';
  el.querySelectorAll('.tab-btn').forEach(function(btn){
    btn.addEventListener('click', function(){ activeTab=btn.dataset.tab; buildTabbar(); renderSlide(); window.scrollTo({top:0,behavior:'smooth'}); });
  });
}

/* ================= rendering ================= */
function canProceed(item){ return item.status==='correct'||item.status==='revealed'||item.status==='skipped'; }

function renderSlide(){
  if(!state.tabs[activeTab]){ activeTab=TAB_DEFS[0].id; }
  var ts = state.tabs[activeTab];
  var slides = SLIDES[activeTab];
  if(ts.idx>=slides.length||ts.idx<0) ts.idx=0;
  var idx = ts.idx;
  var slide = slides[idx];
  var item = ts.items[idx];

  var tdef=TAB_DEFS.find(function(t){return t.id===activeTab;});
  document.getElementById('spLabel').textContent = tdef.label+' · Question '+(idx+1)+' of '+slides.length;
  document.getElementById('secSub').textContent = tdef.label+' — '+tdef.sub;
  document.getElementById('spFill').style.width = Math.round(((idx)/(Math.max(slides.length-1,1)))*100)+'%';

  var h='<div class="qcard">';
  if(slide.kind==='mcq' || slide.kind==='ar'){
    h += renderChoiceBody(slide, item, idx);
  } else {
    h += renderBlankBody(slide, item, idx);
  }
  h += '<div class="feedback" id="feedbackBox"></div>';
  if(MODE==='learning' && (item.status==='correct'||item.status==='revealed')) h += solutionHTML(slide);
  h += '</div>';

  document.getElementById('wrap').innerHTML = h;
  wireSlideEvents(slide, item, idx);
  restoreFeedback(item);
  renderNavbar(item);
  updateFab();
  saveState();
}

function solutionHTML(slide){
  if(!slide.sol) return '';
  return '<div class="solution"><div class="sol-h">Solution</div>'+slide.sol.split('\n').map(function(l){ return '<div class="sol-line">'+fr(esc(l))+'</div>'; }).join('')+'</div>';
}
var LETTERS=['a','b','c','d','e','f'];
function chosenHTML(slide,item){
  var opts = slide.kind==='mcq' ? slide.opts : AR_OPTIONS;
  if(item.choice===undefined) return '';
  var ok=item.choice===slide.correct;
  var h='<div class="chosen '+(ok?'ok':'bad')+'"><b>Your answer:</b> ('+LETTERS[item.choice]+') '+fr(esc(opts[item.choice]))+(ok?' ✓':' ✗')+'</div>';
  if(!ok) h+='<div class="chosen ok"><b>Correct answer:</b> ('+LETTERS[slide.correct]+') '+fr(esc(opts[slide.correct]))+'</div>';
  return h;
}
function renderChoiceBody(slide, item, idx){
  var h='<div class="qhead"><div class="qnum">'+(idx+1)+'</div>';
  if(slide.kind==='mcq'){
    h += '<div class="qtext">'+fr(esc(slide.text))+(slide.tag?'<span class="qtag">'+esc(slide.tag)+'</span>':'')+'</div>';
  } else {
    h += '<div class="qtext"><span class="qtag" style="margin-left:0;margin-right:6px;">A / R</span>Assertion (A): '+fr(esc(slide.a))+'<br>Reason (R): '+fr(esc(slide.r))+(slide.tag?'<span class="qtag">'+esc(slide.tag)+'</span>':'')+'</div>';
  }
  h += '</div>';
  if(slide.fig) h += '<div class="fig">'+slide.fig+'</div>';
  var opts = slide.kind==='mcq' ? slide.opts : AR_OPTIONS;
  if(MODE==='quiz') h += '<div class="quiz-hint">Quiz mode — pick an option. The correct answer is revealed once you finish this tab.</div>';
  var locked = MODE==='learning' && (item.status==='correct' || item.status==='revealed');
  h += '<div class="options">';
  opts.forEach(function(opt,i){
    var cls='opt';
    if(locked){
      if(i===slide.correct) cls+=' is-correct';
      else if(item.choice===i) cls+=' is-wrong';
      cls+=' locked';
    }
    if(item.choice===i) cls+=' is-chosen';
    h += '<label class="'+cls+'"><input type="radio" name="choice" value="'+i+'" '+(item.choice===i?'checked':'')+' '+(locked?'disabled':'')+'> <span class="opt-l">('+LETTERS[i]+')</span> <span class="opt-t">'+fr(esc(opt))+'</span>'+(item.choice===i?'<span class="opt-tag">'+(locked?(i===slide.correct?'Your answer ✓':'Your answer ✗'):'Selected')+'</span>':'')+'</label>';
  });
  h += '</div>';
  if(locked) h += chosenHTML(slide,item);
  return h;
}

function renderBlankBody(slide, item, idx){
  var h='<div class="qhead"><div class="qnum">'+(idx+1)+'</div><div class="qtext">';
  if(slide.kind==='case'){ h += '<b>'+esc(slide.title)+'.</b> '+esc(slide.body); }
  else { var pp=fr(esc(slide.p)).split('\n'); h += pp[0]+pp.slice(1).map(function(x){return '<span class="datline">'+x+'</span>';}).join(''); }
  h += (slide.tag?'<span class="qtag">'+esc(slide.tag)+'</span>':'')+'</div>';
  if(slide.marks) h += '<div class="marks-pill">'+slide.marks+'</div>';
  h += '</div>';
  if(slide.fig) h += '<div class="fig">'+slide.fig+'</div>';

  var total = slide.flat.length;
  var hasExpr = slide.flat.some(function(s){ return s.expr===true; });
  var hasFrac = slide.flat.some(function(s){ return ['fv','fe','fl','fm','fi','flist'].indexOf(s.expr)>=0; });
  var blankCount=0; slide.flat.forEach(function(s){ blankCount+=Object.keys(s.a).length; });

  if(MODE==='quiz'){
    h += '<div class="step-badge">'+blankCount+' blank'+(blankCount===1?'':'s')+' in this question</div>';
    h += '<div class="quiz-hint">Quiz mode — fill in what you can. Correct answers are revealed once you finish this tab.</div>';
    if(hasFrac) h += '<div class="quiz-hint">Type fractions like <b>3/4</b> and mixed numbers like <b>2 3/4</b> (whole number, space, fraction).</div>';
    if(hasExpr) h += '<div class="quiz-hint">Type answers like <b>2x-5</b>, <b>x^2-4</b> or <b>3+2i</b>. Use ^ for powers, | | for absolute value and pi for π. Any equivalent form is accepted.</div>';
    h += '<div class="steps">';
    for(var qi=0; qi<total; qi++){
      var qstep = slide.flat[qi];
      var qss = item.stepStates[qi];
      if(qstep.partLabel) h += '<div class="subpart-label">'+esc(qstep.partLabel)+'</div>';
      if(qstep.orDivider) h += '<div class="or-divider">OR</div>';
      var qline = fr(qstep.t);
      Object.keys(qstep.a).forEach(function(bkey){
        var val = qss.inputs[bkey]||'';
        var inp='<input class="blank-input'+(['fv','fe','fl','fm','fi','dec'].indexOf(qstep.expr)>=0?' fr':(qstep.expr==='flist'||qstep.expr==='dlist'||qstep.expr==='glist')?' wide':qstep.expr===true?' expr':(qstep.expr==='words'||qstep.expr==='list'||qstep.expr==='expanded'||qstep.expr==='set'||qstep.expr==='primes'||qstep.expr==='trans'||qstep.expr==='rot'?' wide':''))+'" data-step="'+qi+'" data-bkey="'+bkey+'" value="'+esc(val)+'">';
        qline = qline.replace('__'+bkey+'__', inp);
      });
      if(qstep.fig) h += '<div class="fig">'+qstep.fig+'</div>';
      h += '<div class="step-line">'+qline+'</div>';
    }
    h += '</div>';
    return h;
  }

  if(hasFrac) h += '<div class="quiz-hint">Type fractions like <b>3/4</b> and mixed numbers like <b>2 3/4</b> (whole number, space, fraction).</div>';
  if(hasExpr) h += '<div class="quiz-hint">Type answers like <b>2x-5</b>, <b>x^2-4</b> or <b>3+2i</b>. Use ^ for powers, | | for absolute value and pi for π. Any equivalent form is accepted.</div>';
  var locked = item.status==='correct' || item.status==='revealed';
  var upto = locked ? total-1 : item.curStep;
  h += '<div class="step-badge">Step '+(Math.min(item.curStep,total-1)+1)+' of '+total+'</div>';
  h += '<div class="steps">';
  for(var i=0;i<=upto;i++){
    var step = slide.flat[i];
    var ss = item.stepStates[i];
    if(step.partLabel) h += '<div class="subpart-label">'+esc(step.partLabel)+'</div>';
    if(step.orDivider) h += '<div class="or-divider">OR</div>';
    var resolved = ss.status==='correct' || ss.status==='revealed';
    var line = fr(step.t);
    Object.keys(step.a).forEach(function(bkey){
      var fs = ss.inputs['fs_'+bkey];
      var cls = fs==='correct'?'is-correct':(fs==='wrong'?'is-wrong':'');
      var val = ss.inputs[bkey]||'';
      var dis = resolved ? 'disabled':'';
      var inp='<input class="blank-input '+cls+(['fv','fe','fl','fm','fi','dec'].indexOf(step.expr)>=0?' fr':(step.expr==='flist'||step.expr==='dlist'||step.expr==='glist')?' wide':step.expr===true?' expr':(step.expr==='words'||step.expr==='list'||step.expr==='expanded'||step.expr==='set'||step.expr==='primes'||step.expr==='trans'||step.expr==='rot'?' wide':''))+'" data-step="'+i+'" data-bkey="'+bkey+'" value="'+esc(val)+'" '+dis+'>';
      line = line.replace('__'+bkey+'__', inp);
    });
    if(step.fig) h += '<div class="fig">'+step.fig+'</div>';
    h += '<div class="step-line'+(resolved?' resolved':'')+'">'+line+'</div>';
    if(ss.status==='revealed'){
      var reveals=[];
      Object.keys(step.a).forEach(function(bkey){ reveals.push(bkey+' = '+esc(step.a[bkey])); });
      h += '<div class="reveal-note">correct: '+reveals.join(', ')+'</div>';
    }
  }
  h += '</div>';
  return h;
}

var __flash=null;
function restoreFeedback(item){
  var fb=document.getElementById('feedbackBox'); if(!fb) return;
  if(__flash){ fb.className='feedback show '+__flash.c; fb.innerHTML=__flash.h; __flash=null; return; }
  if(MODE==='quiz'){ fb.className='feedback'; fb.innerHTML=''; return; }
  if(item.status==='correct'){ fb.className='feedback show ok'; fb.innerHTML='<b>All done — correct!</b>'; }
  else if(item.status==='revealed'){ fb.className='feedback show reveal'; fb.innerHTML='<b>Answer revealed above.</b> Move on whenever you’re ready.'; }
  else if(item.status==='skipped'){ fb.className='feedback show retry'; fb.innerHTML='Skipped — you can answer it now and press <b>Check</b>, or come back later from the Question Palette.'; }
  else { fb.className='feedback'; fb.innerHTML=''; }
}

function slideIsAnswered(slide,item){
  if(slide.kind==='mcq'||slide.kind==='ar') return item.choice!==undefined;
  return item.stepStates.some(function(ss){ return Object.keys(ss.inputs).some(function(k){ return k.indexOf('fs_')!==0 && ss.inputs[k] && String(ss.inputs[k]).trim()!==''; }); });
}
function renderNavbar(item){
  var ts = state.tabs[activeTab];
  var slides = SLIDES[activeTab];
  var slide = slides[ts.idx];
  var isLast = ts.idx === slides.length-1;
  var h='';
  h += '<button class="btn" id="btnPrev" '+(ts.idx===0?'disabled':'')+'>&larr; Previous</button>';

  if(MODE==='quiz'){
    h += '<button class="btn" id="btnSkip">Skip</button>';
    h += '<span class="spacer"></span>';
    h += '<button class="btn btn-primary" id="btnNext">'+(isLast?'Finish':'Next →')+'</button>';
  } else {
    h += '<button class="btn" id="btnSkip" '+(item.status!=='unanswered'?'disabled':'')+'>Skip</button>';
    h += '<span class="spacer"></span>';
    h += '<button class="btn btn-primary" id="btnCheck" '+((item.status!=='unanswered'&&item.status!=='skipped')?'disabled':'')+'>Check</button>';
    h += '<button class="btn btn-primary" id="btnNext" '+(canProceed(item)?'':'disabled')+'>'+(isLast?'Finish':'Next →')+'</button>';
  }
  document.getElementById('navbarInner').innerHTML = h;

  document.getElementById('btnPrev').addEventListener('click', function(){ if(ts.idx>0){ ts.idx--; renderSlide(); } });

  if(MODE==='quiz'){
    document.getElementById('btnSkip').addEventListener('click', function(){
      item.status='skipped';
      advanceQuiz(ts, slides);
    });
    document.getElementById('btnNext').addEventListener('click', function(){
      item.status = slideIsAnswered(slide,item) ? 'answered' : 'unanswered';
      advanceQuiz(ts, slides);
    });
  } else {
    document.getElementById('btnSkip').addEventListener('click', function(){
      if(item.status==='unanswered'){ item.status='skipped'; renderSlide(); }
    });
    document.getElementById('btnNext').addEventListener('click', function(){
      if(!canProceed(item)) return;
      if(ts.idx < slides.length-1){ ts.idx++; ts.maxReached=Math.max(ts.maxReached, ts.idx); renderSlide(); }
      else { renderFinished(); }
    });
    document.getElementById('btnCheck').addEventListener('click', function(){ handleCheck(); });
  }
}
function advanceQuiz(ts, slides){
  if(ts.idx < slides.length-1){ ts.idx++; ts.maxReached=Math.max(ts.maxReached, ts.idx); renderSlide(); }
  else { renderFinished(); }
}

function wireSlideEvents(slide, item, idx){
  document.querySelectorAll('input[type="radio"][name="choice"]').forEach(function(r){
    r.addEventListener('change', function(){ item.choice=parseInt(r.value,10); saveState();
      document.querySelectorAll('.opt').forEach(function(l){ l.classList.remove('is-chosen'); var t=l.querySelector('.opt-tag'); if(t) t.remove(); });
      var lab=r.closest('.opt'); lab.classList.add('is-chosen'); var tg=document.createElement('span'); tg.className='opt-tag'; tg.textContent='Selected'; lab.appendChild(tg); });
  });
  document.querySelectorAll('.blank-input').forEach(function(inp){
    inp.addEventListener('input', function(){
      var si=parseInt(inp.dataset.step,10), bk=inp.dataset.bkey;
      item.stepStates[si].inputs[bk]=inp.value;
      saveState();
    });
  });
}

function handleCheck(){
  var ts = state.tabs[activeTab];
  var slide = SLIDES[activeTab][ts.idx];
  var item = ts.items[ts.idx];
  if(item.status==='skipped') item.status='unanswered';
  var fb = document.getElementById('feedbackBox');

  if(slide.kind==='mcq' || slide.kind==='ar'){
    if(item.choice===undefined){ fb.className='feedback show err'; fb.innerHTML='Please choose an option first.'; return; }
    var ok = item.choice===slide.correct;
    if(ok){
      item.status='correct'; playSuccess();
      fb.className='feedback show ok'; fb.innerHTML='<b>Correct!</b>';
    } else {
      item.attempts=(item.attempts||0)+1;
      if(item.attempts>=2){ item.status='revealed'; playReveal(); }
      else { playWrong(); fb.className='feedback show retry'; fb.innerHTML='<b>Not quite — try again</b> (attempt 1 of 2) <span class="attempts-dots"><span class="used"></span><span></span></span>'; __flash={c:'retry',h:'<b>Not quite — try again</b> (attempt 1 of 2) <span class="attempts-dots"><span class="used"></span><span></span></span>'}; }
    }
    renderSlide();
    return;
  }

  // blank / case
  var step = slide.flat[item.curStep];
  var ss = item.stepStates[item.curStep];
  var blanks = Object.keys(step.a);
  var missing = blanks.some(function(k){ return !ss.inputs[k] || String(ss.inputs[k]).trim()===''; });
  if(missing){ fb.className='feedback show err'; fb.innerHTML='Fill in every blank in this step before checking.'; return; }

  var allGood=true;
  blanks.forEach(function(k){
    var good=answerMatches(ss.inputs[k], step.a[k], step.accept, step.expr);
    ss.inputs['fs_'+k]=good?'correct':'wrong';
    if(!good) allGood=false;
  });

  if(allGood){
    ss.status='correct'; playSuccess();
    advanceStepOrFinish(item, slide);
  } else {
    ss.attempts=(ss.attempts||0)+1;
    if(ss.attempts>=2){
      ss.status='revealed'; playReveal();
      advanceStepOrFinish(item, slide);
    } else {
      playWrong();
      fb.className='feedback show retry';
      fb.innerHTML='<b>Not quite — try again</b> (attempt 1 of 2) <span class="attempts-dots"><span class="used"></span><span></span></span>'; __flash={c:'retry',h:'<b>Not quite — try again</b> (attempt 1 of 2) <span class="attempts-dots"><span class="used"></span><span></span></span>'};
      renderSlide();
      return;
    }
  }
  renderSlide();
}

function advanceStepOrFinish(item, slide){
  var total = slide.flat.length;
  var hasExpr = slide.flat.some(function(s){ return s.expr===true; });
  var hasFrac = slide.flat.some(function(s){ return ['fv','fe','fl','fm','fi','flist'].indexOf(s.expr)>=0; });
  if(item.curStep < total-1){
    item.curStep++;
  } else {
    var anyRevealed = item.stepStates.some(function(ss){ return ss.status==='revealed'; });
    item.status = anyRevealed ? 'revealed' : 'correct';
  }
}

/* ================= palette ================= */
var overlay=document.getElementById('overlay');
function statusOf(tabId,i){
  var ts=state.tabs[tabId];
  if(i>ts.maxReached) return 'locked';
  if(i===ts.idx) return 'current';
  return ts.items[i].status==='unanswered' ? 'locked' : ts.items[i].status;
}
function buildPalette(){
  var slides=SLIDES[activeTab];
  document.getElementById('paletteTitle').textContent = TAB_DEFS.find(function(t){return t.id===activeTab;}).label+' · Question palette';
  var body=document.getElementById('paletteBody');
  var html='';
  for(var i=0;i<slides.length;i++){
    html += '<div class="chip" data-status="'+statusOf(activeTab,i)+'" data-idx="'+i+'">'+(i+1)+'</div>';
  }
  body.innerHTML = html;
  body.querySelectorAll('.chip').forEach(function(chip){
    chip.addEventListener('click', function(){
      var i=parseInt(chip.dataset.idx,10);
      var ts=state.tabs[activeTab];
      if(i>ts.maxReached){ showToast('Finish the earlier questions to unlock this one.'); return; }
      ts.idx=i; closePalette(); renderSlide();
    });
  });
}
function openPalette(){ buildPalette(); overlay.classList.add('show'); }
function closePalette(){ overlay.classList.remove('show'); }
var toastTimer;
function showToast(msg){
  var t=document.getElementById('toast'); t.textContent=msg; t.classList.add('show');
  clearTimeout(toastTimer); toastTimer=setTimeout(function(){ t.classList.remove('show'); },2200);
}
document.getElementById('paletteFab').addEventListener('click', openPalette);
document.getElementById('paletteClose').addEventListener('click', closePalette);
overlay.addEventListener('click', function(e){ if(e.target===overlay) closePalette(); });

function updateFab(){
  var slides=SLIDES[activeTab];
  var done=state.tabs[activeTab].items.filter(function(it){ return it.status==='correct'||it.status==='revealed'||it.status==='skipped'; }).length;
  document.getElementById('fabBadge').textContent = done+'/'+slides.length;
}

/* ================= overall progress + finish ================= */
function updateChapterProgress(){
  var total=0, done=0;
  TAB_DEFS.forEach(function(td){
    state.tabs[td.id].items.forEach(function(it){
      total++;
      if(it.status==='correct'||it.status==='revealed'||it.status==='skipped') done++;
    });
  });
  var pct = total>0 ? Math.round((done/total)*100) : 0;
  document.getElementById('cpFill').style.width=pct+'%';
  document.getElementById('cpLabel').textContent=pct+'% complete';
}
function isSlideCorrect(tabId,i){
  var slide=SLIDES[tabId][i], item=state.tabs[tabId].items[i];
  if(slide.kind==='mcq'||slide.kind==='ar') return item.choice===slide.correct;
  return slide.flat.every(function(step,si){
    var ss=item.stepStates[si];
    return Object.keys(step.a).every(function(k){ return answerMatches(ss.inputs[k], step.a[k], step.accept, step.expr); });
  });
}
function isSlideAttempted(tabId,i){
  var slide=SLIDES[tabId][i], item=state.tabs[tabId].items[i];
  if(slide.kind==='mcq'||slide.kind==='ar') return item.choice!==undefined;
  return slide.flat.some(function(step,si){
    var ss=item.stepStates[si];
    return Object.keys(step.a).some(function(k){ return ss.inputs[k] && String(ss.inputs[k]).trim()!==''; });
  });
}
function slideLabel(slide){
  var t = slide.kind==='case' ? slide.title : (slide.kind==='ar' ? slide.a : (slide.p||slide.text||''));
  t = String(t);
  return t.length>90 ? t.slice(0,90)+'…' : t;
}
function slideAnswerText(slide, item, correctSide){
  if(slide.kind==='mcq'||slide.kind==='ar'){
    var opts = slide.kind==='mcq' ? slide.opts : AR_OPTIONS;
    if(correctSide) return '('+LETTERS[slide.correct]+') '+opts[slide.correct];
    return item.choice!==undefined ? '('+LETTERS[item.choice]+') '+opts[item.choice] : '— not attempted —';
  }
  return slide.flat.map(function(step,si){
    var ss=item.stepStates[si];
    return Object.keys(step.a).map(function(k){
      return correctSide ? step.a[k] : (ss.inputs[k] || '—');
    }).join(', ');
  }).join('  |  ');
}

function renderFinished(){
  if(MODE==='quiz'){ renderQuizResults(); return; }
  var ts=state.tabs[activeTab];
  var correct=ts.items.filter(function(i){return i.status==='correct';}).length;
  var revealed=ts.items.filter(function(i){return i.status==='revealed';}).length;
  var skipped=ts.items.filter(function(i){return i.status==='skipped';}).length;
  var h='<div class="qcard done-card"><div class="big">✨</div><h2>Tab complete</h2>';
  h+='<p style="color:var(--ink-soft);font-size:14px;">You worked through all '+ts.items.length+' questions in this tab.</p>';
  if(!ts.recorded){ ts.recorded=true; addRecord('learning', activeTab, correct, revealed, skipped, ts.items.length); }
  h+='<div class="score-pills">'+
     '<span class="score-pill" style="background:var(--success-soft);color:var(--success);">'+correct+' correct</span>'+
     '<span class="score-pill" style="background:var(--danger-soft);color:var(--danger);">'+revealed+' revealed</span>'+
     '<span class="score-pill" style="background:var(--gold-soft);color:var(--retry-text);">'+skipped+' skipped</span></div>'+
     '<button class="btn btn-primary" id="btnReview">Review from question 1</button></div>';
  document.getElementById('wrap').innerHTML=h;
  document.getElementById('navbarInner').innerHTML='';
  document.getElementById('btnReview').addEventListener('click', function(){ ts.idx=0; ts.recorded=false; renderSlide(); });
  updateChapterProgress(); saveState();
}

function renderQuizResults(){
  var ts=state.tabs[activeTab];
  var slides=SLIDES[activeTab];
  var correctCount=0, attemptedCount=0;
  var rowsHtml = slides.map(function(slide,i){
    var item=ts.items[i];
    var ok=isSlideCorrect(activeTab,i);
    var att=isSlideAttempted(activeTab,i);
    if(ok) correctCount++;
    if(att) attemptedCount++;
    var tagCls = ok?'ok':(att?'bad':'na');
    var tagText = ok?'Correct':(att?'Incorrect':'Not attempted');
    var row='<div class="review-row">';
    row+='<span class="review-tag '+tagCls+'">Q'+(i+1)+' · '+tagText+'</span>';
    row+='<div class="review-q">'+fr(esc(slideLabel(slide)))+'</div>';
    row+='<div class="review-ans"><b>Your answer:</b> '+fr(esc(slideAnswerText(slide,item,false)))+'</div>';
    if(!ok) row+='<div class="review-ans" style="color:var(--success);"><b>Correct answer:</b> '+fr(esc(slideAnswerText(slide,item,true)))+'</div>';
    if(slide.sol) row+='<details class="rev-sol"><summary>Show solution</summary>'+solutionHTML(slide)+'</details>';
    row+='</div>';
    return row;
  }).join('');

  addRecord('quiz', activeTab, correctCount, 0, 0, slides.length);
  var h='<div class="qcard done-card" style="text-align:left;">';
  h+='<div style="text-align:center;"><div class="big">🏁</div><h2>Quiz complete</h2>';
  h+='<p style="color:var(--ink-soft);font-size:14px;">'+correctCount+' / '+slides.length+' correct · '+attemptedCount+' attempted</p></div>';
  h+='<div style="margin-top:16px;">'+rowsHtml+'</div>';
  h+='<div style="text-align:center;margin-top:6px;"><button class="btn btn-primary" id="btnReview">Review from question 1</button></div>';
  h+='</div>';
  document.getElementById('wrap').innerHTML=h;
  document.getElementById('navbarInner').innerHTML='';
  document.getElementById('btnReview').addEventListener('click', function(){ ts.idx=0; renderSlide(); });
  playSuccess();
  updateChapterProgress(); saveState();
}

/* ================= mode picker ================= */
function updateModePill(){
  var btn=document.getElementById('modePill');
  if(!btn) return;
  btn.textContent = MODE==='quiz' ? '📝 Quiz Mode · switch' : '📘 Learning Sheet · switch';
}
function showChrome(show){
  document.querySelector('.tabbar').style.display = show?'':'none';
  document.querySelector('.slide-progress').style.display = show?'':'none';
  document.querySelector('.navbar').style.display = show?'':'none';
  document.getElementById('paletteFab').style.display = show?'':'none';
}
function renderModePicker(){
  showChrome(false);
  var wrap=document.getElementById('wrap');
  wrap.innerHTML =
    '<div class="mode-pick">'+
      '<div class="mode-card" data-pick="learning"><div class="mode-icon">📘</div><h3>Learning Sheet</h3>'+
      '<p>Work through each question step by step with instant feedback — two tries, then the correct value is revealed right there so you can keep moving.</p></div>'+
      '<div class="mode-card" data-pick="quiz"><div class="mode-icon">📝</div><h3>Quiz Mode</h3>'+
      '<p>Attempt every question with no hints along the way. Your score and the full answer key are shown together once you finish the tab — just like the real exam.</p></div>'+
    '</div>';
  wrap.querySelectorAll('[data-pick]').forEach(function(card){
    card.addEventListener('click', function(){
      setMode(card.dataset.pick); activeTab='theory';
      document.getElementById('modePill').hidden=false;
      updateModePill();
      showChrome(true);
      buildTabbar();
      renderSlide();
    });
  });
}
document.getElementById('modePill').addEventListener('click', function(){
  if(!appState.mode){ return; }
  setMode(appState.mode==='quiz' ? 'learning' : 'quiz');
  updateModePill();
  showChrome(true);
  buildTabbar();
  renderSlide();
});

/* ================= boot ================= */
var _origRenderSlide = renderSlide;
renderSlide = function(){ _origRenderSlide(); updateChapterProgress(); updateModePill(); };


/* ================= theory tab ================= */
function renderTheory(){
  var wrap=document.getElementById('wrap');
  wrap.innerHTML='<div class="theory">'+fr(THEORY)+'</div>';
  document.querySelector('.slide-progress').style.display='none';
  document.querySelector('.navbar').style.display='none';
  document.getElementById('paletteFab').style.display='none';
  document.getElementById('secSub').textContent='Theory — notes, key ideas and worked examples';
  wrap.querySelectorAll('[data-go]').forEach(function(b){ b.addEventListener('click',function(){ activeTab=b.dataset.go; buildTabbar(); renderSlide(); window.scrollTo({top:0,behavior:'smooth'}); }); });
  wrap.querySelectorAll('[data-jump]').forEach(function(b){ b.addEventListener('click',function(){ var t=document.getElementById(b.dataset.jump); if(t) t.scrollIntoView({behavior:'smooth',block:'start'}); }); });
}
var _rsTheory = renderSlide;
renderSlide = function(){
  if(activeTab==='theory'){ renderTheory(); buildTabbar(); updateChapterProgress(); updateModePill(); saveState(); return; }
  document.querySelector('.slide-progress').style.display='';
  document.querySelector('.navbar').style.display='';
  document.getElementById('paletteFab').style.display='';
  _rsTheory();
};


/* ================= MYP criterion report ================= */
var CRIT_COL={A:'var(--accent-text)',B:'var(--gold)',C:'#8A6FC4',D:'#2F9AA0'};
function critStats(){
  return REPORT.map(function(r){
    var tabId=r[0], slides=SLIDES[tabId], ts=state&&state.tabs[tabId];
    var c=0,w=0,n=0;
    slides.forEach(function(sl,i){
      if(!ts||!ts.items[i]){ n++; return; }
      var it=ts.items[i];
      if(MODE==='learning'){
        if(it.status==='correct') c++; else if(it.status==='revealed') w++; else n++;
      } else {
        if(isSlideCorrect(tabId,i)) c++; else if(isSlideAttempted(tabId,i)) w++; else n++;
      }
    });
    var tot=slides.length, pct=tot?Math.round(c/tot*100):0;
    var lvl=Math.round(c/Math.max(tot,1)*8);
    return {tab:tabId,letter:r[1],name:r[2],c:c,w:w,n:n,tot:tot,pct:pct,lvl:lvl};
  });
}
function arcPath(cx,cy,r,a0,a1){
  if(a1-a0>=Math.PI*2-1e-6){ return 'M'+(cx-r)+','+cy+' a'+r+','+r+' 0 1,0 '+(2*r)+',0 a'+r+','+r+' 0 1,0 '+(-2*r)+',0 Z'; }
  var x0=cx+r*Math.sin(a0), y0=cy-r*Math.cos(a0), x1=cx+r*Math.sin(a1), y1=cy-r*Math.cos(a1);
  return 'M'+cx+','+cy+' L'+x0.toFixed(2)+','+y0.toFixed(2)+' A'+r+','+r+' 0 '+((a1-a0)>Math.PI?1:0)+',1 '+x1.toFixed(2)+','+y1.toFixed(2)+' Z';
}
function pieSVG(parts,size,hole,center,sub){
  var tot=parts.reduce(function(s,p){return s+p.v;},0), cx=size/2, cy=size/2, r=size/2-4, a=0, h='';
  if(!tot){ h+='<circle cx="'+cx+'" cy="'+cy+'" r="'+r+'" style="fill:var(--paper-2);stroke:var(--rule)"/>'; }
  parts.forEach(function(p){ if(!p.v) return; var b=a+p.v/tot*Math.PI*2; h+='<path d="'+arcPath(cx,cy,r,a,b)+'" style="fill:'+p.col+';stroke:var(--card);stroke-width:2"><title>'+esc(p.label)+': '+p.v+'</title></path>'; a=b; });
  if(hole) h+='<circle cx="'+cx+'" cy="'+cy+'" r="'+(r*hole)+'" style="fill:var(--card)"/>';
  if(center) h+='<text x="'+cx+'" y="'+(cy-(sub?4:0))+'" text-anchor="middle" dominant-baseline="middle" style="fill:var(--ink);font:700 '+(size>150?22:15)+'px Fraunces,serif">'+center+'</text>';
  if(sub) h+='<text x="'+cx+'" y="'+(cy+16)+'" text-anchor="middle" style="fill:var(--ink-soft);font:600 11px \'Source Sans 3\',sans-serif">'+sub+'</text>';
  return '<svg viewBox="0 0 '+size+' '+size+'" width="'+size+'" height="'+size+'" role="img">'+h+'</svg>';
}
function band(l){ return l===0?'0':(l<=2?'1–2':(l<=4?'3–4':(l<=6?'5–6':'7–8'))); }
function renderReport(){
  var st=critStats(), totC=0, totQ=0;
  st.forEach(function(s){ totC+=s.c; totQ+=s.tot; });
  var h='<div class="theory">';
  h+='<section class="note"><h2>Chapter test report</h2><p class="lt">'+(MODE==='quiz'?'<b>Quiz mode</b> results: answers are marked when you finish each test tab.':'<b>Learning mode</b> results: a question counts as correct only if you got it without the answer being revealed. Switch to Quiz mode for an exam-style score.')+'</p>';
  h+='<div class="rep-top"><div class="rep-pie">'+pieSVG(st.map(function(s){return {v:s.c,col:CRIT_COL[s.letter],label:'Criterion '+s.letter};}),200,0.55,totC+'/'+totQ,'correct')+'</div>';
  h+='<div class="rep-legend"><div class="rep-cap">Marks earned, by criterion</div>'+st.map(function(s){ return '<div class="rep-li"><span class="sw" style="background:'+CRIT_COL[s.letter]+'"></span><b>'+s.letter+'</b>&nbsp;'+esc(s.name)+'<span class="rep-n">'+s.c+' / '+s.tot+'</span></div>'; }).join('')+'</div></div></section>';
  h+='<div class="rep-grid">'+st.map(function(s){
    return '<div class="rep-card"><div class="rep-h"><span class="crit" style="background:'+CRIT_COL[s.letter]+'">'+s.letter+'</span>'+esc(s.name)+'</div>'+
      '<div class="rep-row">'+pieSVG([{v:s.c,col:'var(--success)',label:'Correct'},{v:s.w,col:'var(--danger)',label:'Incorrect'},{v:s.n,col:'var(--locked)',label:'Not attempted'}],120,0.5,s.pct+'%')+
      '<div class="rep-stats"><div><span class="sw" style="background:var(--success)"></span>Correct <b>'+s.c+'</b></div><div><span class="sw" style="background:var(--danger)"></span>Incorrect <b>'+s.w+'</b></div><div><span class="sw" style="background:var(--locked)"></span>Not attempted <b>'+s.n+'</b></div>'+
      '<div class="rep-lvl">Indicative level <b>'+s.lvl+'</b> / 8 <span>(band '+band(s.lvl)+')</span></div></div></div>'+
      '<button class="hub-btn" data-go="'+s.tab+'">Open Test '+s.letter+' →</button></div>';
  }).join('')+'</div>';
  h+='<p class="rep-note">Indicative level = fraction of questions correct × 8, rounded. It is a practice guide only; your teacher awards the real MYP criterion levels.</p></div>';
  var wrap=document.getElementById('wrap'); wrap.innerHTML=h;
  document.querySelector('.slide-progress').style.display='none';
  document.querySelector('.navbar').style.display='none';
  document.getElementById('paletteFab').style.display='none';
  document.getElementById('secSub').textContent='Report — chapter test results by MYP criterion';
  wrap.querySelectorAll('[data-go]').forEach(function(b){ b.addEventListener('click',function(){ activeTab=b.dataset.go; buildTabbar(); renderSlide(); window.scrollTo({top:0,behavior:'smooth'}); }); });
}
var _rsReport = renderSlide;
renderSlide = function(){
  if(activeTab==='report'){ renderReport(); buildTabbar(); updateChapterProgress(); updateModePill(); saveState(); return; }
  _rsReport();
};


/* ================= skipped-question return ================= */
function firstSkippedIdx(ts){
  for(var i=0;i<ts.items.length;i++){
    var it=ts.items[i];
    if(MODE==='quiz'){ if(!isSlideAttempted(activeTab,i)) return i; }
    else if(it.status==='skipped'||it.status==='unanswered') return i;
  }
  return -1;
}
function skippedList(ts){
  var out=[]; for(var i=0;i<ts.items.length;i++){ var it=ts.items[i];
    if(MODE==='quiz' ? !isSlideAttempted(activeTab,i) : (it.status==='skipped'||it.status==='unanswered')) out.push(i); }
  return out;
}
function renderSkipGate(ts){
  var list=skippedList(ts);
  var h='<div class="qcard done-card"><div class="big">⏭️</div><h2>You skipped '+list.length+' question'+(list.length>1?'s':'')+'</h2>'+
    '<p style="color:var(--ink-soft);font-size:14px;">Answer them now, or submit the tab as it is. Answers are marked only when you submit.</p>'+
    '<div class="skip-chips">'+list.map(function(i){ return '<button class="chip skip-go" data-i="'+i+'">Q'+(i+1)+'</button>'; }).join('')+'</div>'+
    '<div class="skip-btns"><button class="btn btn-primary" id="btnGoSkipped">Answer skipped questions</button><button class="btn" id="btnSubmitAnyway">Submit anyway</button></div></div>';
  document.getElementById('wrap').innerHTML=h;
  document.getElementById('navbarInner').innerHTML='';
  var go=function(i){ ts.idx=i; ts.maxReached=Math.max(ts.maxReached,i); renderSlide(); window.scrollTo({top:0,behavior:'smooth'}); };
  document.getElementById('btnGoSkipped').addEventListener('click',function(){ go(list[0]); });
  document.querySelectorAll('.skip-go').forEach(function(b){ b.addEventListener('click',function(){ go(parseInt(b.dataset.i,10)); }); });
  document.getElementById('btnSubmitAnyway').addEventListener('click',function(){ ts.submitOK=true; renderFinished(); ts.submitOK=false; });
  saveState();
}
var _rfSkip = renderFinished;
renderFinished = function(){
  var ts=state.tabs[activeTab];
  if(MODE==='quiz' && !ts.submitOK && skippedList(ts).length){ renderSkipGate(ts); return; }
  _rfSkip();
  if(MODE==='learning'){
    var list=skippedList(ts);
    if(list.length){
      var card=document.querySelector('.done-card');
      if(card){ var d=document.createElement('div'); d.className='skip-btns';
        d.innerHTML='<button class="btn btn-primary" id="btnGoSkipped">Attempt skipped questions ('+list.length+')</button>';
        card.appendChild(d);
        document.getElementById('btnGoSkipped').addEventListener('click',function(){ ts.idx=list[0]; ts.recorded=false; renderSlide(); window.scrollTo({top:0,behavior:'smooth'}); }); }
    }
  }
};


/* ================= approx answers (physics: within 1%) ================= */
var _amTools = answerMatches;
answerMatches = function(input,answer,accept,expr){
  if(expr==='approx'){
    var n1=parseNum(input); if(n1===null) return false;
    return [answer].concat(accept||[]).some(function(a){ var n2=parseNum(a); if(n2===null) return false; return Math.abs(n1-n2) <= Math.max(0.011*Math.abs(n2), 1e-9); });
  }
  return _amTools(input,answer,accept,expr);
};

/* ================= palette: every question already reached can be opened ================= */
statusOf = function(tabId,i){
  var ts=state.tabs[tabId];
  if(i>ts.maxReached) return 'locked';
  if(i===ts.idx) return 'current';
  var s=ts.items[i].status;
  if(s==='unanswered') return 'skipped';
  return s;
};

/* ================= on-screen keyboard ================= */
var KB={on:true, page:'num', target:null};
try{ var kbp=localStorage.getItem('sopaan-kb-pref'); if(kbp==='off') KB.on=false; }catch(e){}
function kbSave(){ try{ localStorage.setItem('sopaan-kb-pref', KB.on?'on':'off'); }catch(e){} }
var KEYS_NUM=[['7','8','9','(',')'],['4','5','6','−','/'],['1','2','3','.',','],['0',':','%','°','⌫'],['abc','←','→','Clear','Done']];
var KEYS_FRAC=[['7','8','9','/'],['4','5','6','−'],['1','2','3','space'],['0',',','⌫','Clear'],['abc','←','→','Done']];
var KEYS_ALG=[['7','8','9','x','y','n'],['4','5','6','+','−','a'],['1','2','3','×','÷','b'],['0','.','(',')','^','²'],['/','π','|','t','⌫','Clear'],['abc','←','→','Done']];
function kbLayoutFor(inp){ try{ var ts=state.tabs[activeTab], sl=SLIDES[activeTab][ts.idx], stp=sl.flat[parseInt(inp.dataset.step,10)]; var m=stp.expr, key=String(stp.a[inp.dataset.bkey]||'');
  if(m==='words'||m==='glist'||m==='angle') return 'abc'; if(m===true||m==='pow'||m==='primes') return 'alg';
  if(['fv','fe','fl','fm','fi','flist'].indexOf(m)>=0) return 'frac'; if(m==='dec'||m==='approx'||m==='dlist'||m==='set'||m==='coord'||m==='list'||m==='time') return 'num';
  if(/^[\-−]?\d+ \d+\/\d+$/.test(key)||/^[\-−]?\d+\/\d+$/.test(key)) return 'frac'; if(/[a-df-z]/i.test(key.replace(/pi/gi,''))) return /\d/.test(key)?'alg':'abc'; return 'num'; }catch(e){ return 'num'; } }
var KEYS_ABC=[['q','w','e','r','t','y','u','i','o','p'],['a','s','d','f','g','h','j','k','l','-'],['z','x','c','v','b','n','m',',',':','/'],['123','space','←','→','⌫','Done']];
function kbBuild(){
  var el=document.getElementById('vkb'); if(!el){ el=document.createElement('div'); el.id='vkb'; el.className='vkb'; document.body.appendChild(el);
    el.addEventListener('pointerdown',function(e){ var b=e.target.closest('button[data-k]'); e.preventDefault(); if(b) kbPress(b.dataset.k); });
    el.addEventListener('mousedown',function(e){ e.preventDefault(); }); }
  var rows={num:KEYS_NUM,frac:KEYS_FRAC,alg:KEYS_ALG,abc:KEYS_ABC}[KB.page]||KEYS_NUM;
  el.innerHTML='<div class="vkb-top"><span>⌨️ Keyboard</span><button data-k="device" class="vkb-link">Use device keyboard</button></div>'+
    rows.map(function(r){ return '<div class="vkb-row">'+r.map(function(k){
      var cls='vkb-k'+(/^(abc|123|Done|Clear|⌫|←|→|space)$/.test(k)?' fn':'')+(k==='Done'?' done':'');
      return '<button type="button" class="'+cls+'" data-k="'+k+'">'+(k==='space'?'space':k)+'</button>'; }).join('')+'</div>'; }).join('');
  return el;
}
function kbShow(inp){ KB.target=inp; KB.home=kbLayoutFor(inp); KB.page=KB.home; if(!KB.on) return; var cp=document.getElementById('calcPanel'); if(cp&&cp.classList.contains('show')) return; var el=kbBuild(); var nb=document.querySelector('.navbar'); el.style.bottom=(nb?nb.getBoundingClientRect().height:0)+'px'; el.classList.add('show'); document.body.classList.add('kb-open'); setTimeout(function(){ var r=inp.getBoundingClientRect(), top=el.getBoundingClientRect().top; if(r.bottom>top-12) window.scrollBy({top:r.bottom-top+60,behavior:'smooth'}); else if(r.top<60) window.scrollBy({top:r.top-80,behavior:'smooth'}); },30); }
function kbHide(){ var el=document.getElementById('vkb'); if(el) el.classList.remove('show'); document.body.classList.remove('kb-open'); }
function kbInsert(s){
  var t=KB.target; if(!t||t.disabled) return;
  var a=t.selectionStart==null?t.value.length:t.selectionStart, b=t.selectionEnd==null?a:t.selectionEnd;
  t.value=t.value.slice(0,a)+s+t.value.slice(b); var p=a+s.length; try{ t.setSelectionRange(p,p); }catch(e){}
  t.dispatchEvent(new Event('input',{bubbles:true}));
}
function kbPress(k){
  var t=KB.target; if(k==='device'){ KB.on=false; kbSave(); kbHide(); document.querySelectorAll('.blank-input').forEach(function(i){ i.removeAttribute('inputmode'); }); if(t){ t.blur(); setTimeout(function(){ t.focus(); },50); } showToast('Device keyboard on. Tap ⌨️ on any blank to bring the on-screen keyboard back.'); return; }
  if(k==='Done'){ kbHide(); if(t) t.blur(); return; }
  if(k==='abc'||k==='123'){ KB.page=(k==='abc')?'abc':(KB.home&&KB.home!=='abc'?KB.home:'num'); kbBuild(); return; }
  if(!t) return;
  if(k==='⌫'){ var a=t.selectionStart, b=t.selectionEnd; if(a===b&&a>0){ t.value=t.value.slice(0,a-1)+t.value.slice(b); try{t.setSelectionRange(a-1,a-1);}catch(e){} } else { t.value=t.value.slice(0,a)+t.value.slice(b); try{t.setSelectionRange(a,a);}catch(e){} } t.dispatchEvent(new Event('input',{bubbles:true})); return; }
  if(k==='Clear'){ t.value=''; t.dispatchEvent(new Event('input',{bubbles:true})); return; }
  if(k==='←'||k==='→'){ var p=(t.selectionStart||0)+(k==='←'?-1:1); p=Math.max(0,Math.min(t.value.length,p)); try{t.setSelectionRange(p,p);}catch(e){} return; }
  var map={'−':'-','space':' '}; kbInsert(map[k]!==undefined?map[k]:k);
}
function kbWire(){
  document.querySelectorAll('.blank-input').forEach(function(inp){
    if(inp.dataset.kb) return; inp.dataset.kb='1';
    if(KB.on) inp.setAttribute('inputmode','none');
    inp.addEventListener('focus',function(){ kbShow(inp); });
    var btn=document.createElement('button'); btn.type='button'; btn.className='kb-toggle'; btn.title='On-screen keyboard'; btn.textContent='⌨️'; btn.tabIndex=-1;
    btn.addEventListener('mousedown',function(e){ e.preventDefault(); });
    btn.addEventListener('click',function(){ KB.on=true; kbSave(); document.querySelectorAll('.blank-input').forEach(function(i){ i.setAttribute('inputmode','none'); }); inp.focus(); kbShow(inp); });
    if(!inp.disabled) inp.insertAdjacentElement('afterend',btn);
  });
}
document.addEventListener('focusout',function(e){ setTimeout(function(){ var a=document.activeElement; if(!a||!a.classList||!a.classList.contains('blank-input')){ if(!document.querySelector('#vkb:hover')) kbHide(); } },120); });

/* ================= calculator ================= */
var CALC={expr:'', ans:0};
function calcEval(src){
  var s=String(src).replace(/×/g,'*').replace(/÷/g,'/').replace(/−/g,'-').replace(/π/g,'(PI)').replace(/Ans/g,'('+CALC.ans+')').replace(/\^/g,'**').replace(/√\(/g,'sqrt(').replace(/²/g,'**2').replace(/E/g,'*10**');
  s=s.replace(/(^|[(*\/+\-,])-/g,'$1(-1)*');
  if(/[^0-9+\-*/().,a-z A-Z]/.test(s)) throw 0;
  var ok=s.replace(/sin|cos|tan|asin|acos|atan|sqrt|log|ln|PI|abs/g,''); if(/[a-zA-Z]/.test(ok)) throw 0;
  var f=new Function('sin','cos','tan','asin','acos','atan','sqrt','log','ln','PI','abs','return ('+s+');');
  var d=Math.PI/180;
  var v=f(function(x){return Math.sin(x*d);},function(x){return Math.cos(x*d);},function(x){return Math.tan(x*d);},
    function(x){return Math.asin(x)/d;},function(x){return Math.acos(x)/d;},function(x){return Math.atan(x)/d;},Math.sqrt,Math.log10,Math.log,Math.PI,Math.abs);
  if(typeof v!=='number'||!isFinite(v)) throw 0; return v;
}
function fmtNum(v){ if(Math.abs(v)>=1e10||(Math.abs(v)<1e-6&&v!==0)) return v.toExponential(6).replace(/\.?0+e/,'e'); return String(parseFloat(v.toPrecision(10))); }
var CKEYS=[['sin(','cos(','tan(','√(','^','²'],['asin(','acos(','atan(','(',')','π'],['7','8','9','÷','⌫','AC'],['4','5','6','×','E','Ans'],['1','2','3','−','(−)','Insert'],['0','.','=','+']];
function openCalc(){
  var p=document.getElementById('calcPanel');
  if(!p){ p=document.createElement('div'); p.id='calcPanel'; p.className='tool-panel calc';
    p.innerHTML='<div class="tp-head"><b>🧮 Calculator</b><span class="tp-note">degrees · tap a blank, then Insert</span><button class="tp-x" data-c="close">✕</button></div>'+
      '<div class="calc-disp"><div class="calc-expr" id="calcExpr"></div><div class="calc-res" id="calcRes">0</div></div>'+
      '<div class="calc-keys">'+CKEYS.map(function(r){ return r.map(function(k){ return '<button type="button" data-c="'+k+'" class="'+(k==='='?'eq':(/^(AC|⌫|Insert)$/.test(k)?'fn':''))+'">'+({'sin(':'sin','cos(':'cos','tan(':'tan','asin(':'sin⁻¹','acos(':'cos⁻¹','atan(':'tan⁻¹','√(':'√'}[k]||k)+'</button>'; }).join(''); }).join('')+'</div>';
    document.body.appendChild(p);
    p.addEventListener('mousedown',function(e){ if(e.target.closest('button')) e.preventDefault(); });
    p.addEventListener('click',function(e){ var b=e.target.closest('button[data-c]'); if(!b) return; calcKey(b.dataset.c); });
  }
  kbHide(); var nb=document.querySelector('.navbar'); p.style.bottom=((nb?nb.getBoundingClientRect().height:0)+8)+'px'; p.classList.add('show'); document.body.classList.add('calc-open'); calcShow();
}
function calcShow(res){ document.getElementById('calcExpr').textContent=CALC.expr||' '; if(res!==undefined) document.getElementById('calcRes').textContent=res; }
function calcKey(k){
  if(k==='close'){ document.getElementById('calcPanel').classList.remove('show'); document.body.classList.remove('calc-open'); return; }
  if(k==='AC'){ CALC.expr=''; calcShow('0'); return; }
  if(k==='⌫'){ CALC.expr=CALC.expr.replace(/(asin\(|acos\(|atan\(|sin\(|cos\(|tan\(|√\(|Ans|.)$/,''); calcShow(); return; }
  if(k==='='){ try{ var v=calcEval(CALC.expr); CALC.ans=v; calcShow(fmtNum(v)); }catch(e){ calcShow('Error'); } return; }
  if(k==='(−)'){ CALC.expr+='−'; calcShow(); return; }
  if(k==='Insert'){ var r=document.getElementById('calcRes').textContent; if(KB.target && !KB.target.disabled && r!=='Error'){ KB.target.value=r; KB.target.dispatchEvent(new Event('input',{bubbles:true})); showToast('Inserted '+r+' into the blank.'); } else showToast('Tap a blank first, then press Insert.'); return; }
  CALC.expr+=k; calcShow();
}

/* ================= Desmos ================= */
var DESMOS_KEY='dcb31709b452b1cf9dc26972add0fda6', desmosCalc=null, desmosLoading=false;
function openDesmos(exprs){
  var p=document.getElementById('desmosPanel');
  if(!p){ p=document.createElement('div'); p.id='desmosPanel'; p.className='tool-panel desmos';
    p.innerHTML='<div class="tp-head"><b>📈 Desmos graphing calculator</b><button class="tp-x" id="desmosReset">Reset graph</button><button class="tp-x" id="desmosClose">✕</button></div><div id="desmosBox"><div class="desmos-msg">Loading Desmos…</div></div>';
    document.body.appendChild(p);
    document.getElementById('desmosClose').addEventListener('click',function(){ p.classList.remove('show'); });
    document.getElementById('desmosReset').addEventListener('click',function(){ if(desmosCalc) desmosSet(p._exprs||[]); });
  }
  p._exprs=exprs||[]; p.classList.add('show');
  if(window.Desmos){ desmosInit(); desmosSet(p._exprs); return; }
  if(desmosLoading) return; desmosLoading=true;
  var sc=document.createElement('script'); sc.src='https://www.desmos.com/api/v1.9/calculator.js?apiKey='+DESMOS_KEY;
  sc.onload=function(){ desmosInit(); desmosSet(p._exprs); };
  sc.onerror=function(){ desmosLoading=false; document.getElementById('desmosBox').innerHTML='<div class="desmos-msg">Desmos needs an internet connection. <a href="https://www.desmos.com/calculator" target="_blank" rel="noopener">Open Desmos in a new tab</a>.</div>'; };
  document.head.appendChild(sc);
}
function desmosInit(){ if(desmosCalc) return; var box=document.getElementById('desmosBox'); box.innerHTML=''; desmosCalc=Desmos.GraphingCalculator(box,{expressionsCollapsed:false,settingsMenu:false,border:false,degreeMode:true}); }
function desmosSet(exprs){ if(!desmosCalc) return; desmosCalc.setBlank(); (exprs||[]).forEach(function(e,i){ if(typeof e==='string') desmosCalc.setExpression({id:'e'+i,latex:e}); else desmosCalc.setExpression(Object.assign({id:'e'+i},e)); }); }

/* ================= toolbar on each question ================= */
var _rsTools = renderSlide;
renderSlide = function(){
  _rsTools();
  kbHide();
  if(activeTab==='theory'||activeTab==='report') return;
  var ts=state.tabs[activeTab]; if(!ts) return;
  var slide=SLIDES[activeTab][ts.idx], card=document.querySelector('#wrap .qcard');
  if(card && slide && slide.tools && slide.tools.length && !card.querySelector('.tool-bar')){
    var bar=document.createElement('div'); bar.className='tool-bar';
    bar.innerHTML=(slide.tools.indexOf('calc')>=0?'<button type="button" class="tool-btn" data-t="calc">🧮 Calculator</button>':'')+
                  (slide.tools.indexOf('desmos')>=0?'<button type="button" class="tool-btn" data-t="desmos">📈 Desmos graph</button>':'');
    card.insertBefore(bar, card.firstChild);
    bar.addEventListener('click',function(e){ var b=e.target.closest('[data-t]'); if(!b) return; if(b.dataset.t==='calc') openCalc(); else openDesmos(slide.desmos||[]); });
  }
  kbWire();
};



/* ================= signed fractions in text: {−3/4}, {3/−4}, {−2 1/3}, {p/q} ================= */
fr = function(s){ return String(s).replace(/&lt;(\/?)(b|sup|sub|i)>/g,'<$1$2>')
  .replace(/\{([−-]?\d+) (\d+)\/(\d+)\}/g,'<span class="mx">$1<span class="fq"><span>$2</span><span>$3</span></span></span>')
  .replace(/\{([−-]?[A-Za-z0-9]+)\/([−-]?[A-Za-z0-9]+)\}/g,'<span class="fq"><span>$1</span><span>$2</span></span>'); };
/* ================= BMA badge → main page of this sheet (theory hub) ================= */
(function(){
  var c=document.querySelector('.brand .crest'); if(!c) return;
  var a=document.createElement('button'); a.type='button'; a.className='crest crest-home'; a.title='Back to the main page (theory notes)'; a.setAttribute('aria-label','Main page');
  a.innerHTML='BM<span class="crest-h">⌂</span>'; c.parentNode.replaceChild(a,c);
  a.addEventListener('click',function(){
    if(!student||!MODE){ window.scrollTo({top:0,behavior:'smooth'}); return; }
    if(typeof kbHide==='function') kbHide(); if(typeof SP!=='undefined'&&SP.on) spToggle(false);
    var cp=document.getElementById('calcPanel'); if(cp) cp.classList.remove('show'); document.body.classList.remove('calc-open');
    activeTab = (typeof THEORY!=='undefined') ? 'theory' : TAB_DEFS[0].id;
    buildTabbar(); renderSlide(); window.scrollTo({top:0,behavior:'smooth'});
  });
})();

/* ================= session clock: starts at sign-in and keeps running ================= */
var CLK={t0:null};
(function(){
  var row=document.querySelector('.brand .brand-row'); if(!row) return;
  var d=document.createElement('div'); d.className='bmasw off'; d.id='swBox'; d.title='Time since you signed in';
  d.innerHTML='<span class="bmasw-ic">⏱</span><span class="bmasw-t" id="swT">00:00</span>';
  row.appendChild(d); setInterval(swTick,1000);
})();
function swFmt(s){ s=Math.floor(s||0); var h=Math.floor(s/3600), m=Math.floor(s%3600/60), x=s%60; return (h?h+':'+String(m).padStart(2,'0'):String(m).padStart(2,'0'))+':'+String(x).padStart(2,'0'); }
function swTick(){
  var box=document.getElementById('swBox'); if(!box) return;
  if(student && !CLK.t0) CLK.t0=Date.now();
  if(!student) CLK.t0=null;
  box.classList.toggle('off',!CLK.t0);
  document.getElementById('swT').textContent = CLK.t0 ? swFmt((Date.now()-CLK.t0)/1000) : '00:00';
}
function swTab(){ try{ if(!state||!state.tabs||activeTab==='theory'||activeTab==='report') return null; return state.tabs[activeTab]||null; }catch(e){ return null; } }
var _rsSW = renderSlide;
renderSlide = function(){ _rsSW(); swTick(); };
var _rfSW = renderFinished;
renderFinished = function(){ _rfSW(); var done=document.querySelector('#wrap .done-card'); if(CLK.t0 && done && !done.querySelector('.bmasw-done')){ var p=document.createElement('p'); p.className='bmasw-done'; p.textContent='⏱ Time since sign-in: '+swFmt((Date.now()-CLK.t0)/1000); var h2=done.querySelector('h2'); if(h2) h2.insertAdjacentElement('afterend',p); else done.appendChild(p); } };

/* ================= scratchpad (Khan-style, 4 pens) ================= */
var SP={on:false, draw:true, color:'ink', size:3, erase:false, store:{}, key:null, cv:null, ctx:null, down:false, last:null};
var SP_COL={ink:null, blue:'#2563EB', red:'#DC2626', green:'#16A34A'};
function spInk(){ return getComputedStyle(document.documentElement).getPropertyValue('--ink').trim()||'#211E1A'; }
function spKey(){ var ts=swTab(); return ts ? (MODE+'|'+activeTab+'|'+ts.idx) : null; }
function spBuild(){
  if(SP.cv) return;
  var cv=document.createElement('canvas'); cv.id='spCanvas'; cv.className='sp-canvas'; document.body.appendChild(cv);
  var bar=document.createElement('div'); bar.id='spBar'; bar.className='sp-bar';
  bar.innerHTML='<span class="sp-lbl">✏️ Scratchpad</span>'+
    ['ink','blue','red','green'].map(function(c){ return '<button type="button" class="sp-pen" data-c="'+c+'" title="'+(c==='ink'?'black':c)+' pen"><i style="background:'+(c==='ink'?'var(--ink)':SP_COL[c])+'"></i></button>'; }).join('')+
    '<button type="button" class="sp-tool" data-t="erase" title="Eraser">🧽</button><button type="button" class="sp-tool" data-t="size" title="Pen size">●</button><button type="button" class="sp-tool" data-t="scroll" title="Pause drawing to scroll or answer">✋</button>'+
    '<button type="button" class="sp-tool" data-t="clear" title="Clear page">🗑</button><button type="button" class="sp-tool" data-t="close" title="Close scratchpad">✕</button>';
  document.body.appendChild(bar);
  bar.addEventListener('click',function(e){ var b=e.target.closest('button'); if(!b) return;
    if(b.dataset.c){ SP.color=b.dataset.c; SP.erase=false; SP.draw=true; }
    else if(b.dataset.t==='erase'){ SP.erase=true; SP.draw=true; }
    else if(b.dataset.t==='size'){ SP.size = SP.size===3?6:(SP.size===6?1.5:3); b.textContent = SP.size===6?'⬤':(SP.size===1.5?'·':'●'); }
    else if(b.dataset.t==='scroll'){ SP.draw=!SP.draw; }
    else if(b.dataset.t==='clear'){ spClear(); }
    else if(b.dataset.t==='close'){ spToggle(false); return; }
    spUI(); });
  SP.cv=cv; SP.ctx=cv.getContext('2d');
  cv.addEventListener('pointerdown',function(e){ if(!SP.draw) return; e.preventDefault(); cv.setPointerCapture(e.pointerId); SP.down=true; SP.last=spPt(e); spDot(SP.last); });
  cv.addEventListener('pointermove',function(e){ if(!SP.down) return; e.preventDefault(); var p=spPt(e); spLine(SP.last,p); SP.last=p; });
  var up=function(){ if(SP.down){ SP.down=false; spSave(); } };
  cv.addEventListener('pointerup',up); cv.addEventListener('pointercancel',up); cv.addEventListener('pointerleave',up);
  window.addEventListener('resize',function(){ if(SP.on) spFit(true); });
}
function spPt(e){ var r=SP.cv.getBoundingClientRect(); return {x:e.clientX-r.left, y:e.clientY-r.top}; }
function spStyle(){ var c=SP.ctx; c.lineCap='round'; c.lineJoin='round'; c.globalCompositeOperation=SP.erase?'destination-out':'source-over'; c.strokeStyle=c.fillStyle=(SP.color==='ink'?spInk():SP_COL[SP.color]); c.lineWidth=SP.erase?22:SP.size; }
function spDot(p){ spStyle(); var c=SP.ctx; c.beginPath(); c.arc(p.x,p.y,(SP.erase?11:SP.size/2),0,Math.PI*2); c.fill(); }
function spLine(a,b){ spStyle(); var c=SP.ctx; c.beginPath(); c.moveTo(a.x,a.y); c.lineTo(b.x,b.y); c.stroke(); }
function spSave(){ if(SP.key&&SP.cv){ try{ SP.store[SP.key]=SP.cv.toDataURL(); }catch(e){} } }
function spClear(){ if(!SP.ctx) return; SP.ctx.save(); SP.ctx.setTransform(1,0,0,1,0,0); SP.ctx.clearRect(0,0,SP.cv.width,SP.cv.height); SP.ctx.restore(); if(SP.key) delete SP.store[SP.key]; }
function spFit(keep){
  var wrap=document.getElementById('wrap'); if(!wrap||!SP.cv) return;
  var r=wrap.getBoundingClientRect(), top=r.top+window.scrollY, h=Math.max(wrap.scrollHeight, window.innerHeight-r.top)+40, w=document.documentElement.clientWidth;
  var old=keep&&SP.key?SP.store[SP.key]:null, dpr=window.devicePixelRatio||1;
  SP.cv.style.top=top+'px'; SP.cv.style.left='0px'; SP.cv.style.width=w+'px'; SP.cv.style.height=h+'px';
  SP.cv.width=Math.round(w*dpr); SP.cv.height=Math.round(h*dpr); SP.ctx.setTransform(dpr,0,0,dpr,0,0);
  if(old){ var im=new Image(); im.onload=function(){ SP.ctx.save(); SP.ctx.setTransform(1,0,0,1,0,0); SP.ctx.drawImage(im,0,0); SP.ctx.restore(); }; im.src=old; }
}
function spLoad(){ spSave(); SP.key=spKey(); spFit(false); var d=SP.key&&SP.store[SP.key]; if(d){ var im=new Image(); im.onload=function(){ SP.ctx.save(); SP.ctx.setTransform(1,0,0,1,0,0); SP.ctx.drawImage(im,0,0); SP.ctx.restore(); }; im.src=d; } }
function spUI(){
  var bar=document.getElementById('spBar'); if(!bar) return;
  bar.querySelectorAll('.sp-pen').forEach(function(b){ b.classList.toggle('on', !SP.erase && SP.draw && b.dataset.c===SP.color); });
  bar.querySelector('[data-t=erase]').classList.toggle('on', SP.erase && SP.draw);
  bar.querySelector('[data-t=scroll]').classList.toggle('on', !SP.draw);
  SP.cv.classList.toggle('passive', !SP.draw);
  var fb=document.getElementById('spFab'); if(fb) fb.classList.toggle('on',SP.on);
}
function spToggle(on){
  spBuild(); SP.on=(on===undefined)?!SP.on:on;
  document.body.classList.toggle('sp-open',SP.on); SP.cv.style.display=SP.on?'block':'none'; document.getElementById('spBar').style.display=SP.on?'flex':'none';
  if(SP.on){ SP.draw=true; SP.erase=false; spLoad(); if(typeof kbHide==='function') kbHide(); } else { spSave(); }
  spUI();
}
(function(){ var f=document.createElement('button'); f.type='button'; f.id='spFab'; f.className='sp-fab'; f.innerHTML='✏️ <span>Scratchpad</span>'; f.title='Open a scratchpad to write your working'; f.addEventListener('click',function(){ spToggle(); }); document.body.appendChild(f); })();
var _rsSP = renderSlide;
renderSlide = function(){ _rsSP(); var fab=document.getElementById('spFab'); var q=!!swTab(); if(fab) fab.style.display=q?'':'none'; if(!q && SP.on) spToggle(false); if(SP.on) setTimeout(spLoad,30); };

renderLogin();
})();
</script>
</body>
</html>
