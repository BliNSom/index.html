<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Examen EMS — LimiteRP</title>
<link href="https://fonts.googleapis.com/css2?family=Bebas+Neue&family=DM+Sans:ital,wght@0,300;0,400;0,500;0,600;1,300&display=swap" rel="stylesheet">
<style>
:root{
  --red:#e03030;--red-dark:#b01818;--red-glow:rgba(224,48,48,0.18);
  --bg:#0a0c0f;--surface:#11151a;--surface2:#181d24;--surface3:#1e242d;
  --border:rgba(255,255,255,0.07);--border-bright:rgba(224,48,48,0.4);
  --text:#e8eaf0;--text-muted:#6b7585;--accent:#f0c040;
  --green:#2ecc71;--green-bg:rgba(46,204,113,0.1);--green-border:rgba(46,204,113,0.3);
  --blue:#4aa8ff;--blue-bg:rgba(74,168,255,0.1);
}
*,*::before,*::after{box-sizing:border-box;margin:0;padding:0}
body{background:var(--bg);color:var(--text);font-family:'DM Sans',sans-serif;font-size:15px;line-height:1.6;min-height:100vh;overflow-x:hidden}
body::before{content:'';position:fixed;inset:0;background-image:url("data:image/svg+xml,%3Csvg viewBox='0 0 200 200' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.85' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)' opacity='0.04'/%3E%3C/svg%3E");pointer-events:none;z-index:0}

/* HERO */
.hero{position:relative;background:linear-gradient(135deg,#0d1117 0%,#1a0505 50%,#0d1117 100%);border-bottom:2px solid var(--red);padding:48px 24px 40px;text-align:center;overflow:hidden}
.hero::after{content:'';position:absolute;bottom:-1px;left:50%;transform:translateX(-50%);width:300px;height:2px;background:var(--red);box-shadow:0 0 30px 8px var(--red-glow)}
.hero-badge{display:inline-block;font-size:11px;font-weight:600;letter-spacing:.2em;text-transform:uppercase;color:var(--red);border:1px solid var(--border-bright);background:rgba(224,48,48,.08);padding:4px 16px;border-radius:2px;margin-bottom:16px}
.hero h1{font-family:'Bebas Neue',sans-serif;font-size:clamp(42px,8vw,80px);letter-spacing:.05em;line-height:1;color:#fff;text-shadow:0 0 40px rgba(224,48,48,.4);margin-bottom:8px}
.hero h1 span{color:var(--red)}
.hero-sub{font-size:13px;color:var(--text-muted);letter-spacing:.12em;text-transform:uppercase;margin-top:10px}
.hero-cross{position:absolute;right:32px;top:50%;transform:translateY(-50%);opacity:.06;font-size:120px;line-height:1;font-family:'Bebas Neue',sans-serif;color:var(--red);pointer-events:none;user-select:none}

/* LAYOUT */
.container{max-width:860px;margin:0 auto;padding:40px 20px 80px;position:relative;z-index:1}
.section-label{display:flex;align-items:center;gap:12px;margin:40px 0 20px}
.section-label .num{font-family:'Bebas Neue',sans-serif;font-size:13px;background:var(--red);color:#fff;padding:2px 10px;letter-spacing:.1em;border-radius:2px}
.section-label h2{font-family:'Bebas Neue',sans-serif;font-size:22px;letter-spacing:.08em;color:#fff}
.section-label::after{content:'';flex:1;height:1px;background:var(--border)}
.card{background:var(--surface);border:1px solid var(--border);border-radius:6px;padding:28px 28px 24px;margin-bottom:16px}
.grid-2{display:grid;grid-template-columns:1fr 1fr;gap:16px}
@media(max-width:600px){.grid-2{grid-template-columns:1fr}}
.field{display:flex;flex-direction:column;gap:6px}
label{font-size:11px;font-weight:600;letter-spacing:.12em;text-transform:uppercase;color:var(--text-muted)}
input[type=text],input[type=tel],input[type=date],input[type=password],textarea,select{background:var(--surface2);border:1px solid var(--border);border-radius:4px;color:var(--text);font-family:'DM Sans',sans-serif;font-size:14px;padding:10px 14px;width:100%;outline:none;transition:border-color .2s,box-shadow .2s;-webkit-appearance:none}
input:focus,textarea:focus,select:focus{border-color:var(--red);box-shadow:0 0 0 3px var(--red-glow)}
textarea{resize:vertical;min-height:80px}

/* RADIO TOGGLE */
.radio-group{display:flex;gap:12px;flex-wrap:wrap}
.radio-option{flex:1;min-width:100px}
.radio-option input[type=radio]{display:none}
.radio-option label{display:block;background:var(--surface2);border:1px solid var(--border);border-radius:4px;padding:10px 16px;cursor:pointer;text-align:center;font-size:13px;text-transform:none;letter-spacing:0;font-weight:500;color:var(--text-muted);transition:all .2s}
.radio-option input[type=radio]:checked+label{border-color:var(--red);background:rgba(224,48,48,.12);color:var(--red);box-shadow:0 0 0 1px var(--red)}

/* QUESTION CARDS */
.question-card{background:var(--surface);border:1px solid var(--border);border-left:3px solid var(--red);border-radius:6px;padding:22px 22px 18px;margin-bottom:14px;transition:border-color .2s}
.question-card:hover{border-color:rgba(224,48,48,.3)}
.q-header{display:flex;align-items:flex-start;gap:14px;margin-bottom:14px}
.q-num{font-family:'Bebas Neue',sans-serif;font-size:28px;color:var(--red);line-height:1;min-width:36px;flex-shrink:0}
.q-text{font-size:15px;font-weight:500;color:var(--text);line-height:1.5}
.choices{display:flex;flex-direction:column;gap:8px}
.choice-option input[type=radio]{display:none}
.choice-option label{display:flex;align-items:center;gap:12px;background:var(--surface2);border:1px solid var(--border);border-radius:4px;padding:10px 14px;cursor:pointer;font-size:14px;text-transform:none;letter-spacing:0;font-weight:400;color:var(--text);transition:all .15s}
.choice-option label::before{content:'';width:16px;height:16px;border-radius:50%;border:2px solid var(--border);flex-shrink:0;transition:all .15s}
.choice-option input[type=radio]:checked+label{border-color:var(--red);background:rgba(224,48,48,.08)}
.choice-option input[type=radio]:checked+label::before{background:var(--red);border-color:var(--red);box-shadow:0 0 0 3px var(--red-glow)}
.answer-area{margin-top:12px}
.answer-area>p{font-size:11px;color:var(--text-muted);font-style:italic;margin-bottom:6px}
.answer-area textarea{min-height:60px;font-size:13px}

/* SUBMIT */
.submit-wrap{text-align:center;margin-top:48px}
.btn-submit{display:inline-flex;align-items:center;gap:10px;background:var(--red);color:#fff;border:none;cursor:pointer;font-family:'Bebas Neue',sans-serif;font-size:20px;letter-spacing:.12em;padding:16px 48px;border-radius:4px;transition:all .2s;text-transform:uppercase;box-shadow:0 4px 24px rgba(224,48,48,.3)}
.btn-submit:hover{background:var(--red-dark);box-shadow:0 6px 32px rgba(224,48,48,.5);transform:translateY(-1px)}
.btn-submit:disabled{opacity:.5;cursor:not-allowed;transform:none}
.note-sm{font-size:12px;color:var(--text-muted);font-style:italic}
.divider{height:1px;background:var(--border);margin:32px 0}

/* SUCCESS */
#success{display:none;text-align:center;padding:80px 20px;animation:fadeIn .5s ease}
.success-icon{font-size:64px;margin-bottom:20px;display:block}
#success h2{font-family:'Bebas Neue',sans-serif;font-size:36px;letter-spacing:.08em;color:var(--green);margin-bottom:12px}
#success p{color:var(--text-muted);font-size:15px;max-width:460px;margin:0 auto;line-height:1.7}

/* ══════════════════════════════
   ADMIN PANEL
══════════════════════════════ */
#admin-panel{display:none;position:relative;z-index:1}
.admin-topbar{background:var(--surface);border-bottom:2px solid var(--accent);padding:16px 24px;display:flex;align-items:center;justify-content:space-between;gap:12px;flex-wrap:wrap;position:sticky;top:0;z-index:50}
.admin-topbar-left{display:flex;align-items:center;gap:16px}
.admin-logo{font-family:'Bebas Neue',sans-serif;font-size:22px;letter-spacing:.1em;color:var(--accent)}
.admin-logo span{color:var(--red)}
.admin-topbar-right{display:flex;gap:10px;flex-wrap:wrap}
.btn-sm{font-family:'DM Sans',sans-serif;font-size:12px;font-weight:600;padding:7px 14px;border-radius:4px;cursor:pointer;transition:all .2s;border:1px solid var(--border);background:var(--surface2);color:var(--text-muted);letter-spacing:.05em}
.btn-sm:hover{color:var(--text);border-color:var(--text-muted)}
.btn-sm.danger{border-color:rgba(224,48,48,.4);color:var(--red)}
.btn-sm.danger:hover{background:rgba(224,48,48,.1)}
.btn-sm.accent{border-color:rgba(240,192,64,.4);color:var(--accent)}
.btn-sm.accent:hover{background:rgba(240,192,64,.08)}

.admin-body{max-width:1100px;margin:0 auto;padding:28px 20px 80px}

/* Stat bar */
.stat-row{display:flex;gap:12px;margin-bottom:24px;flex-wrap:wrap}
.stat-box{background:var(--surface);border:1px solid var(--border);border-radius:6px;padding:14px 20px;min-width:110px;text-align:center;flex:1}
.stat-num{font-family:'Bebas Neue',sans-serif;font-size:34px;line-height:1}
.stat-lbl{font-size:10px;letter-spacing:.12em;text-transform:uppercase;color:var(--text-muted);margin-top:2px}

/* Filter / search bar */
.filter-bar{display:flex;gap:10px;margin-bottom:20px;flex-wrap:wrap;align-items:center}
.filter-bar input{flex:1;min-width:180px;height:38px;font-size:13px}
.filter-bar select{height:38px;font-size:13px;width:auto;flex:0 0 auto}
.filter-count{font-size:12px;color:var(--text-muted);white-space:nowrap}

/* Exam cards */
.exam-card{background:var(--surface);border:1px solid var(--border);border-radius:8px;margin-bottom:14px;overflow:hidden;transition:border-color .2s}
.exam-card:hover{border-color:rgba(224,48,48,.2)}
.exam-header{display:flex;align-items:center;gap:12px;padding:14px 18px;background:var(--surface2);cursor:pointer;flex-wrap:wrap}
.exam-header:hover{background:var(--surface3)}
.exam-name{font-weight:600;font-size:15px;color:#fff;flex:1;min-width:120px}
.exam-meta-row{display:flex;gap:12px;font-size:12px;color:var(--text-muted);flex-wrap:wrap;margin-top:3px}
.badge{font-size:10px;font-weight:700;letter-spacing:.1em;padding:3px 10px;border-radius:20px;text-transform:uppercase;white-space:nowrap}
.badge-pass{background:var(--green-bg);color:var(--green);border:1px solid var(--green-border)}
.badge-fail{background:rgba(224,48,48,.12);color:var(--red);border:1px solid rgba(224,48,48,.3)}
.badge-pending{background:rgba(240,192,64,.1);color:var(--accent);border:1px solid rgba(240,192,64,.3)}
.score-pill{font-family:'Bebas Neue',sans-serif;font-size:20px;line-height:1;padding:0 8px}
.score-good{color:var(--green)}
.score-bad{color:var(--red)}
.exam-toggle{font-size:18px;color:var(--red);margin-left:auto;flex-shrink:0}

.exam-body{display:none;padding:20px}
.exam-body.open{display:block;animation:fadeIn .2s ease}

/* Info grid */
.info-grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(150px,1fr));gap:10px;margin-bottom:20px;padding-bottom:18px;border-bottom:1px solid var(--border)}
.info-item label{font-size:10px;letter-spacing:.1em;text-transform:uppercase;color:var(--text-muted);display:block;margin-bottom:2px}
.info-item span{font-size:13px;color:var(--text);font-weight:500}

/* Score overview */
.score-overview{display:flex;align-items:center;justify-content:space-between;background:var(--surface2);border-radius:6px;padding:14px 18px;margin-bottom:18px;flex-wrap:wrap;gap:12px;border:1px solid var(--border)}
.score-big{font-family:'Bebas Neue',sans-serif;font-size:44px;line-height:1}
.score-bar-wrap{flex:1;min-width:150px}
.score-bar-bg{height:8px;background:var(--border);border-radius:4px;overflow:hidden;margin-bottom:4px}
.score-bar-fill{height:100%;border-radius:4px;transition:width .5s ease}
.score-bar-fill.good{background:var(--green)}
.score-bar-fill.bad{background:var(--red)}

/* Answer rows */
.answers-section h4{font-family:'Bebas Neue',sans-serif;font-size:16px;letter-spacing:.08em;color:var(--text-muted);margin-bottom:12px}
.ans-row{margin-bottom:12px;padding-bottom:12px;border-bottom:1px solid var(--border)}
.ans-row:last-child{border-bottom:none;margin-bottom:0;padding-bottom:0}
.ans-qnum{font-size:10px;font-weight:700;letter-spacing:.1em;color:var(--red);text-transform:uppercase;margin-bottom:2px}
.ans-qtext{font-size:12px;color:var(--text-muted);margin-bottom:6px;font-style:italic}
.ans-chosen{display:flex;align-items:flex-start;gap:8px;margin-bottom:4px}
.ans-mark{font-size:16px;flex-shrink:0;margin-top:3px}
.ans-box{flex:1;font-size:13px;background:var(--surface2);border-radius:4px;padding:7px 12px;border-left:3px solid var(--border)}
.ans-box.correct{border-left-color:var(--green)}
.ans-box.wrong{border-left-color:var(--red)}
.ans-correct-row{font-size:12px;color:var(--green);background:var(--green-bg);border:1px solid var(--green-border);border-radius:4px;padding:5px 10px;margin-top:3px}
.ans-comment{font-size:12px;color:var(--text-muted);background:var(--surface2);border-left:3px solid var(--text-muted);border-radius:4px;padding:6px 10px;margin-top:4px;font-style:italic}

/* Result sender */
.result-panel{background:var(--surface2);border:1px solid var(--border-bright);border-radius:6px;padding:18px 20px;margin-top:18px}
.result-panel h4{font-family:'Bebas Neue',sans-serif;font-size:18px;letter-spacing:.08em;color:var(--accent);margin-bottom:8px}
.result-panel p{font-size:13px;color:var(--text-muted);margin-bottom:12px}
.result-note-box{width:100%;margin-bottom:10px;font-size:13px;min-height:60px}
.result-btn-row{display:flex;gap:10px;flex-wrap:wrap;margin-bottom:10px}
.btn-approve{background:rgba(46,204,113,.15);color:var(--green);border:1px solid var(--green-border);font-family:'DM Sans',sans-serif;font-weight:600;font-size:13px;padding:10px 18px;border-radius:4px;cursor:pointer;transition:all .2s}
.btn-approve:hover{background:rgba(46,204,113,.25)}
.btn-reject{background:rgba(224,48,48,.1);color:var(--red);border:1px solid rgba(224,48,48,.35);font-family:'DM Sans',sans-serif;font-weight:600;font-size:13px;padding:10px 18px;border-radius:4px;cursor:pointer;transition:all .2s}
.btn-reject:hover{background:rgba(224,48,48,.2)}
.btn-reset-res{background:transparent;border:1px solid var(--border);color:var(--text-muted);font-family:'DM Sans',sans-serif;font-size:13px;padding:10px 14px;border-radius:4px;cursor:pointer;transition:all .2s}
.btn-reset-res:hover{border-color:var(--text-muted);color:var(--text)}
.result-sent-box{border-radius:4px;padding:10px 14px;font-size:13px;display:none}
.result-sent-box.show{display:block}
.result-sent-box.pass{background:var(--green-bg);border:1px solid var(--green-border);color:var(--green)}
.result-sent-box.fail{background:rgba(224,48,48,.1);border:1px solid rgba(224,48,48,.3);color:var(--red)}

/* Quick-correct tool */
.quick-tool{background:var(--surface3);border:1px solid var(--border);border-radius:6px;padding:14px 18px;margin-top:12px}
.quick-tool h5{font-size:12px;font-weight:700;letter-spacing:.1em;text-transform:uppercase;color:var(--accent);margin-bottom:8px}
.quick-tool-row{display:flex;align-items:center;gap:8px;flex-wrap:wrap}
.override-select{font-size:12px;height:32px;padding:0 10px;width:auto;flex:0 0 auto}
.btn-override{font-size:12px;padding:6px 12px;background:rgba(240,192,64,.12);border:1px solid rgba(240,192,64,.3);color:var(--accent);border-radius:4px;cursor:pointer;font-family:'DM Sans',sans-serif;font-weight:600;transition:all .2s}
.btn-override:hover{background:rgba(240,192,64,.22)}
.override-note{font-size:11px;color:var(--text-muted);width:100%;margin-top:4px}

/* Notes tool */
.admin-notes-area{margin-top:12px}
.admin-notes-area label{font-size:11px;color:var(--text-muted);display:block;margin-bottom:4px;text-transform:none;letter-spacing:0;font-weight:400;font-style:italic}
.admin-notes-area textarea{min-height:50px;font-size:12px}
.btn-save-note{font-size:11px;padding:5px 12px;background:var(--blue-bg);border:1px solid rgba(74,168,255,.3);color:var(--blue);border-radius:4px;cursor:pointer;font-family:'DM Sans',sans-serif;margin-top:6px;transition:all .2s}
.btn-save-note:hover{background:rgba(74,168,255,.2)}

/* Empty state */
.empty-state{text-align:center;padding:60px 20px;color:var(--text-muted)}
.empty-state .big{font-size:52px;margin-bottom:12px}
.empty-state p{font-size:14px}

/* ADMIN LOCK */
#admin-lock{position:fixed;bottom:24px;right:24px;z-index:100}
.btn-admin-trigger{background:var(--surface2);border:1px solid var(--border);color:var(--text-muted);font-size:11px;font-family:'DM Sans',sans-serif;letter-spacing:.1em;text-transform:uppercase;padding:9px 18px;border-radius:4px;cursor:pointer;transition:all .2s}
.btn-admin-trigger:hover{border-color:var(--accent);color:var(--accent)}

/* MODAL */
.modal-overlay{display:none;position:fixed;inset:0;background:rgba(0,0,0,.8);z-index:200;align-items:center;justify-content:center}
.modal-overlay.open{display:flex}
.modal-box{background:var(--surface);border:1px solid var(--border-bright);border-radius:8px;padding:32px;width:360px;max-width:90vw;text-align:center;box-shadow:0 0 40px rgba(224,48,48,.2)}
.modal-box h3{font-family:'Bebas Neue',sans-serif;font-size:24px;letter-spacing:.08em;color:var(--accent);margin-bottom:10px}
.modal-box p{font-size:13px;color:var(--text-muted);margin-bottom:16px}
.modal-err{font-size:12px;color:var(--red);min-height:16px;display:block;margin-bottom:10px}
.btn-modal-ok{background:var(--red);color:#fff;border:none;font-family:'Bebas Neue',sans-serif;font-size:18px;letter-spacing:.1em;padding:12px 32px;border-radius:4px;cursor:pointer;width:100%;margin-bottom:10px}
.btn-modal-ok:hover{background:var(--red-dark)}
.btn-modal-cancel{background:none;border:none;color:var(--text-muted);cursor:pointer;font-size:13px}

/* SHARE BANNER */
.share-banner{background:var(--surface2);border:1px solid var(--border);border-radius:6px;padding:16px 20px;margin-bottom:24px;display:flex;align-items:center;gap:14px;flex-wrap:wrap}
.share-banner .share-icon{font-size:24px;flex-shrink:0}
.share-banner-text{flex:1}
.share-banner-text h4{font-size:13px;font-weight:700;color:var(--text);margin-bottom:2px}
.share-banner-text p{font-size:12px;color:var(--text-muted)}
.share-url-box{display:flex;gap:8px;margin-top:8px;align-items:center;flex-wrap:wrap}
.share-url-input{flex:1;min-width:200px;height:34px;font-size:12px;color:var(--accent);background:var(--surface);border-color:rgba(240,192,64,.25)}
.btn-copy{font-size:12px;height:34px;padding:0 14px;background:rgba(240,192,64,.1);border:1px solid rgba(240,192,64,.3);color:var(--accent);border-radius:4px;cursor:pointer;white-space:nowrap;font-family:'DM Sans',sans-serif;font-weight:600;transition:all .2s}
.btn-copy:hover{background:rgba(240,192,64,.2)}
.btn-copy.copied{background:var(--green-bg);border-color:var(--green-border);color:var(--green)}

/* SETUP MODAL */
.setup-modal{display:none;position:fixed;inset:0;background:rgba(0,0,0,.85);z-index:300;align-items:flex-start;justify-content:center;overflow-y:auto;padding:20px}
.setup-modal.open{display:flex}
.setup-box{background:var(--surface);border:1px solid var(--border-bright);border-radius:10px;padding:32px;width:560px;max-width:98vw;margin:auto}
.setup-box h3{font-family:'Bebas Neue',sans-serif;font-size:26px;letter-spacing:.08em;color:var(--accent);margin-bottom:6px}
.setup-box>p{font-size:13px;color:var(--text-muted);margin-bottom:20px;line-height:1.6}
.setup-step{background:var(--surface2);border:1px solid var(--border);border-radius:6px;padding:16px;margin-bottom:12px}
.setup-step h4{font-size:13px;font-weight:700;color:var(--text);margin-bottom:6px}
.setup-step p{font-size:12px;color:var(--text-muted);line-height:1.6;margin-bottom:8px}
.setup-step a{color:var(--blue);text-decoration:none}
.setup-step a:hover{text-decoration:underline}
.setup-step code{background:var(--surface3);border:1px solid var(--border);border-radius:3px;padding:2px 6px;font-size:11px;color:var(--accent);font-family:monospace}
.setup-step textarea{min-height:80px;font-size:12px;font-family:monospace;color:var(--accent)}
.btn-setup-save{background:var(--red);color:#fff;border:none;font-family:'Bebas Neue',sans-serif;font-size:18px;letter-spacing:.1em;padding:12px 32px;border-radius:4px;cursor:pointer;width:100%;margin-top:8px}
.btn-setup-save:hover{background:var(--red-dark)}

@keyframes fadeIn{from{opacity:0;transform:translateY(6px)}to{opacity:1;transform:translateY(0)}}
</style>
</head>
<body>

<!-- ═══════════════════════════════════════════
     HERO
════════════════════════════════════════════ -->
<div class="hero">
  <div class="hero-cross">✚</div>
  <div class="hero-badge">Reclutamiento Oficial</div>
  <h1>Examen <span>EMS</span></h1>
  <div class="hero-sub">LimiteRP — Servicio de Emergencias Médicas</div>
</div>

<!-- ═══════════════════════════════════════════
     EXAM FORM
════════════════════════════════════════════ -->
<div class="container" id="exam-container">
  <p class="note-sm" style="margin-bottom:8px;">Completa todos los campos. Este examen es parte del proceso oficial de ingreso al Servicio de Emergencias Médicas de LimiteRP.</p>

  <form id="exam-form">

    <!-- DATOS -->
    <div class="section-label">
      <span class="num">I</span>
      <h2>Datos del Solicitante</h2>
    </div>
    <div class="card">
      <div class="grid-2" style="margin-bottom:16px">
        <div class="field">
          <label for="f-name">Nombre completo (Rol)</label>
          <input type="text" id="f-name" name="name" placeholder="Ej: Carlos Medina" required>
        </div>
        <div class="field">
          <label for="f-phone">Teléfono en la ciudad</label>
          <input type="tel" id="f-phone" name="phone" placeholder="Ej: 555-1234" required>
        </div>
      </div>
      <div class="grid-2" style="margin-bottom:16px">
        <div class="field">
          <label for="f-date">Fecha de solicitud</label>
          <input type="date" id="f-date" name="date" required>
        </div>
        <div class="field">
          <label>¿Experiencia previa como médico o paramédico?</label>
          <div class="radio-group" style="margin-top:4px">
            <div class="radio-option"><input type="radio" name="experience" id="exp-yes" value="Sí" required><label for="exp-yes">✓ Sí, tengo experiencia</label></div>
            <div class="radio-option"><input type="radio" name="experience" id="exp-no" value="No"><label for="exp-no">✗ Primera vez</label></div>
          </div>
        </div>
      </div>
      <div class="field">
        <label for="f-bio">¿Por qué quieres unirte al EMS?</label>
        <textarea id="f-bio" name="bio" placeholder="Cuéntanos tu motivación y qué esperas del servicio..." required></textarea>
      </div>
    </div>

    <!-- PREGUNTAS -->
    <div class="section-label">
      <span class="num">II</span>
      <h2>Examen — 15 Preguntas</h2>
    </div>
    <p class="note-sm" style="margin-bottom:20px">Selecciona la mejor respuesta. Puedes dejar un comentario opcional debajo de cada pregunta.</p>

    <!-- Q1 -->
    <div class="question-card">
      <div class="q-header"><div class="q-num">01</div><div class="q-text">Recibes una llamada al radio: hay una persona tirada en el suelo en el centro y no responde. ¿Qué es lo primero que debes hacer al llegar?</div></div>
      <div class="choices">
        <div class="choice-option"><input type="radio" name="q1" id="q1a" value="A"><label for="q1a">A) Empezar a revisar las heridas directamente</label></div>
        <div class="choice-option"><input type="radio" name="q1" id="q1b" value="B"><label for="q1b">B) Asegurarte de que el área es segura y verificar si la persona respira</label></div>
        <div class="choice-option"><input type="radio" name="q1" id="q1c" value="C"><label for="q1c">C) Darle agua y esperar que reaccione</label></div>
        <div class="choice-option"><input type="radio" name="q1" id="q1d" value="D"><label for="q1d">D) Llamar a la policía y esperar a que lleguen primero</label></div>
      </div>
      <div class="answer-area"><p>Comentario opcional:</p><textarea name="q1_exp" placeholder="Tu comentario..."></textarea></div>
    </div>

    <!-- Q2 -->
    <div class="question-card">
      <div class="q-header"><div class="q-num">02</div><div class="q-text">Una persona fue herida de bala en el brazo y está sangrando mucho. ¿Qué haces primero para controlar el sangrado?</div></div>
      <div class="choices">
        <div class="choice-option"><input type="radio" name="q2" id="q2a" value="A"><label for="q2a">A) Limpiar la herida con agua antes de tocarla</label></div>
        <div class="choice-option"><input type="radio" name="q2" id="q2b" value="B"><label for="q2b">B) Presionar fuerte sobre la herida con un trapo o venda para detener la sangre</label></div>
        <div class="choice-option"><input type="radio" name="q2" id="q2c" value="C"><label for="q2c">C) Subir las piernas de la persona al aire</label></div>
        <div class="choice-option"><input type="radio" name="q2" id="q2d" value="D"><label for="q2d">D) Llevarlo al hospital sin hacer nada antes</label></div>
      </div>
      <div class="answer-area"><p>Comentario opcional:</p><textarea name="q2_exp" placeholder="Tu comentario..."></textarea></div>
    </div>

    <!-- Q3 -->
    <div class="question-card">
      <div class="q-header"><div class="q-num">03</div><div class="q-text">Llegas a una escena y la persona está inconsciente pero todavía respira. ¿En qué posición la colocas mientras esperas ayuda?</div></div>
      <div class="choices">
        <div class="choice-option"><input type="radio" name="q3" id="q3a" value="A"><label for="q3a">A) Sentada con la espalda recta</label></div>
        <div class="choice-option"><input type="radio" name="q3" id="q3b" value="B"><label for="q3b">B) De lado (posición de recuperación), para que no se ahogue si vomita</label></div>
        <div class="choice-option"><input type="radio" name="q3" id="q3c" value="C"><label for="q3c">C) Boca arriba con los brazos extendidos</label></div>
        <div class="choice-option"><input type="radio" name="q3" id="q3d" value="D"><label for="q3d">D) De pie apoyada en algo</label></div>
      </div>
      <div class="answer-area"><p>Comentario opcional:</p><textarea name="q3_exp" placeholder="Tu comentario..."></textarea></div>
    </div>

    <!-- Q4 — ORIGINAL FAVORITA -->
    <div class="question-card">
      <div class="q-header"><div class="q-num">04</div><div class="q-text">Una persona no respira y no tiene pulso. Decides hacer RCP. ¿Qué incluye el RCP básico?</div></div>
      <div class="choices">
        <div class="choice-option"><input type="radio" name="q4" id="q4a" value="A"><label for="q4a">A) Solo respiraciones de boca a boca</label></div>
        <div class="choice-option"><input type="radio" name="q4" id="q4b" value="B"><label for="q4b">B) Solo presionar el pecho repetidamente</label></div>
        <div class="choice-option"><input type="radio" name="q4" id="q4c" value="C"><label for="q4c">C) Compresiones en el pecho y respiraciones (o solo compresiones si estás solo)</label></div>
        <div class="choice-option"><input type="radio" name="q4" id="q4d" value="D"><label for="q4d">D) Agitar a la persona para que reaccione</label></div>
      </div>
      <div class="answer-area"><p>Comentario opcional:</p><textarea name="q4_exp" placeholder="Tu comentario..."></textarea></div>
    </div>

    <!-- Q5 -->
    <div class="question-card">
      <div class="q-header"><div class="q-num">05</div><div class="q-text">Atiendes a alguien que tuvo un accidente de carro y dice que le duele mucho el cuello. ¿Qué es importante evitar?</div></div>
      <div class="choices">
        <div class="choice-option"><input type="radio" name="q5" id="q5a" value="A"><label for="q5a">A) Moverle el cuello o la cabeza sin necesidad</label></div>
        <div class="choice-option"><input type="radio" name="q5" id="q5b" value="B"><label for="q5b">B) Hablarle para mantenerlo calmado</label></div>
        <div class="choice-option"><input type="radio" name="q5" id="q5c" value="C"><label for="q5c">C) Revisar sus signos vitales</label></div>
        <div class="choice-option"><input type="radio" name="q5" id="q5d" value="D"><label for="q5d">D) Pedir apoyo por radio</label></div>
      </div>
      <div class="answer-area"><p>Comentario opcional:</p><textarea name="q5_exp" placeholder="Tu comentario..."></textarea></div>
    </div>

    <!-- Q6 — ORIGINAL FAVORITA -->
    <div class="question-card">
      <div class="q-header"><div class="q-num">06</div><div class="q-text">Ves a alguien en la calle que de repente empieza a convulsionar (le tiembla todo el cuerpo sin control). ¿Qué haces?</div></div>
      <div class="choices">
        <div class="choice-option"><input type="radio" name="q6" id="q6a" value="A"><label for="q6a">A) Sujetarle los brazos para que no se mueva</label></div>
        <div class="choice-option"><input type="radio" name="q6" id="q6b" value="B"><label for="q6b">B) Alejar objetos peligrosos, ponerlo de lado y esperar a que pase sin forzarlo</label></div>
        <div class="choice-option"><input type="radio" name="q6" id="q6c" value="C"><label for="q6c">C) Meterle algo en la boca para que no se muerda la lengua</label></div>
        <div class="choice-option"><input type="radio" name="q6" id="q6d" value="D"><label for="q6d">D) Darle agua inmediatamente</label></div>
      </div>
      <div class="answer-area"><p>Comentario opcional:</p><textarea name="q6_exp" placeholder="Tu comentario..."></textarea></div>
    </div>

    <!-- Q7 -->
    <div class="question-card">
      <div class="q-header"><div class="q-num">07</div><div class="q-text">Alguien tiene una quemadura en el brazo por un incendio. ¿Qué haces primero?</div></div>
      <div class="choices">
        <div class="choice-option"><input type="radio" name="q7" id="q7a" value="A"><label for="q7a">A) Poner hielo directo sobre la quemadura</label></div>
        <div class="choice-option"><input type="radio" name="q7" id="q7b" value="B"><label for="q7b">B) Enfriar la zona con agua fría (no helada) durante unos minutos</label></div>
        <div class="choice-option"><input type="radio" name="q7" id="q7c" value="C"><label for="q7c">C) Pinchar las ampollas para que no se llenen</label></div>
        <div class="choice-option"><input type="radio" name="q7" id="q7d" value="D"><label for="q7d">D) Cubrir con una venda muy apretada de inmediato</label></div>
      </div>
      <div class="answer-area"><p>Comentario opcional:</p><textarea name="q7_exp" placeholder="Tu comentario..."></textarea></div>
    </div>

    <!-- Q8 — ORIGINAL FAVORITA -->
    <div class="question-card">
      <div class="q-header"><div class="q-num">08</div><div class="q-text">Como médico del EMS, ¿puedes contarle a alguien en la calle el estado de salud de tu paciente sin su permiso?</div></div>
      <div class="choices">
        <div class="choice-option"><input type="radio" name="q8" id="q8a" value="A"><label for="q8a">A) Sí, siempre que la persona lo pida</label></div>
        <div class="choice-option"><input type="radio" name="q8" id="q8b" value="B"><label for="q8b">B) No, la información del paciente es confidencial</label></div>
        <div class="choice-option"><input type="radio" name="q8" id="q8c" value="C"><label for="q8c">C) Sí, porque así todos están informados</label></div>
        <div class="choice-option"><input type="radio" name="q8" id="q8d" value="D"><label for="q8d">D) Solo si la persona que pregunta es amigo del paciente</label></div>
      </div>
      <div class="answer-area"><p>Comentario opcional:</p><textarea name="q8_exp" placeholder="Tu comentario..."></textarea></div>
    </div>

    <!-- Q9 -->
    <div class="question-card">
      <div class="q-header"><div class="q-num">09</div><div class="q-text">¿Qué significa que una persona esté "en shock" después de perder mucha sangre?</div></div>
      <div class="choices">
        <div class="choice-option"><input type="radio" name="q9" id="q9a" value="A"><label for="q9a">A) Que está muy asustada emocionalmente</label></div>
        <div class="choice-option"><input type="radio" name="q9" id="q9b" value="B"><label for="q9b">B) Que su cuerpo no tiene suficiente sangre para funcionar bien — es una emergencia grave</label></div>
        <div class="choice-option"><input type="radio" name="q9" id="q9c" value="C"><label for="q9c">C) Que necesita comer algo</label></div>
        <div class="choice-option"><input type="radio" name="q9" id="q9d" value="D"><label for="q9d">D) Que ya se está recuperando</label></div>
      </div>
      <div class="answer-area"><p>Comentario opcional:</p><textarea name="q9_exp" placeholder="Tu comentario..."></textarea></div>
    </div>

    <!-- Q10 -->
    <div class="question-card">
      <div class="q-header"><div class="q-num">10</div><div class="q-text">Un ciudadano al que estás atendiendo te pregunta si va a estar bien. Tú no estás seguro todavía. ¿Qué le dices?</div></div>
      <div class="choices">
        <div class="choice-option"><input type="radio" name="q10" id="q10a" value="A"><label for="q10a">A) "Vas a estar perfectamente bien, no te preocupes"</label></div>
        <div class="choice-option"><input type="radio" name="q10" id="q10b" value="B"><label for="q10b">B) "Estamos haciendo todo lo posible, quédate tranquilo"</label></div>
        <div class="choice-option"><input type="radio" name="q10" id="q10c" value="C"><label for="q10c">C) "No sé nada, espera"</label></div>
        <div class="choice-option"><input type="radio" name="q10" id="q10d" value="D"><label for="q10d">D) Ignorarlo y seguir trabajando sin responderle</label></div>
      </div>
      <div class="answer-area"><p>Comentario opcional:</p><textarea name="q10_exp" placeholder="Tu comentario..."></textarea></div>
    </div>

    <!-- Q11 -->
    <div class="question-card">
      <div class="q-header"><div class="q-num">11</div><div class="q-text">Llegas a atender a alguien que resulta ser un criminal conocido en la ciudad. ¿Qué haces?</div></div>
      <div class="choices">
        <div class="choice-option"><input type="radio" name="q11" id="q11a" value="A"><label for="q11a">A) Te niegas a atenderlo por su historial</label></div>
        <div class="choice-option"><input type="radio" name="q11" id="q11b" value="B"><label for="q11b">B) Lo atiendes igual que a cualquier otro — el EMS atiende a todos</label></div>
        <div class="choice-option"><input type="radio" name="q11" id="q11c" value="C"><label for="q11c">C) Llamas a la policía primero y esperas su autorización</label></div>
        <div class="choice-option"><input type="radio" name="q11" id="q11d" value="D"><label for="q11d">D) Solo lo atiendes si la policía está presente</label></div>
      </div>
      <div class="answer-area"><p>Comentario opcional:</p><textarea name="q11_exp" placeholder="Tu comentario..."></textarea></div>
    </div>

    <!-- Q12 -->
    <div class="question-card">
      <div class="q-header"><div class="q-num">12</div><div class="q-text">Alguien está atrapado en un vehículo accidentado y no puedes moverlo de inmediato. ¿Qué haces mientras esperas apoyo?</div></div>
      <div class="choices">
        <div class="choice-option"><input type="radio" name="q12" id="q12a" value="A"><label for="q12a">A) Jalarlo fuerte para sacarlo lo antes posible</label></div>
        <div class="choice-option"><input type="radio" name="q12" id="q12b" value="B"><label for="q12b">B) Mantenerlo calmado, controlar el sangrado si hay, y esperar apoyo especializado</label></div>
        <div class="choice-option"><input type="radio" name="q12" id="q12c" value="C"><label for="q12c">C) Dejarlo solo hasta que llegue la policía</label></div>
        <div class="choice-option"><input type="radio" name="q12" id="q12d" value="D"><label for="q12d">D) Darle medicamentos sin saber qué tiene</label></div>
      </div>
      <div class="answer-area"><p>Comentario opcional:</p><textarea name="q12_exp" placeholder="Tu comentario..."></textarea></div>
    </div>

    <!-- Q13 -->
    <div class="question-card">
      <div class="q-header"><div class="q-num">13</div><div class="q-text">Una persona dice que le duele mucho el pecho, tiene los labios morados y le falta el aire. ¿Qué sospechas?</div></div>
      <div class="choices">
        <div class="choice-option"><input type="radio" name="q13" id="q13a" value="A"><label for="q13a">A) Que tiene hambre</label></div>
        <div class="choice-option"><input type="radio" name="q13" id="q13b" value="B"><label for="q13b">B) Puede estar teniendo un problema cardíaco o respiratorio grave</label></div>
        <div class="choice-option"><input type="radio" name="q13" id="q13c" value="C"><label for="q13c">C) Que está actuando para llamar la atención</label></div>
        <div class="choice-option"><input type="radio" name="q13" id="q13d" value="D"><label for="q13d">D) Que se deshidrató por correr</label></div>
      </div>
      <div class="answer-area"><p>Comentario opcional:</p><textarea name="q13_exp" placeholder="Tu comentario..."></textarea></div>
    </div>

    <!-- Q14 -->
    <div class="question-card">
      <div class="q-header"><div class="q-num">14</div><div class="q-text">Terminas de atender a alguien y el paciente está estable. ¿Cuál es el paso correcto antes de irte de la escena?</div></div>
      <div class="choices">
        <div class="choice-option"><input type="radio" name="q14" id="q14a" value="A"><label for="q14a">A) Irte de inmediato al próximo llamado</label></div>
        <div class="choice-option"><input type="radio" name="q14" id="q14b" value="B"><label for="q14b">B) Confirmar por radio que terminaste, asegurarte de que el paciente está estable y hacer el reporte</label></div>
        <div class="choice-option"><input type="radio" name="q14" id="q14c" value="C"><label for="q14c">C) Esperar que la policía te dé el visto bueno</label></div>
        <div class="choice-option"><input type="radio" name="q14" id="q14d" value="D"><label for="q14d">D) No es necesario hacer nada más</label></div>
      </div>
      <div class="answer-area"><p>Comentario opcional:</p><textarea name="q14_exp" placeholder="Tu comentario..."></textarea></div>
    </div>

    <!-- Q15 — ORIGINAL FAVORITA -->
    <div class="question-card">
      <div class="q-header"><div class="q-num">15</div><div class="q-text">Llegas a una escena de tiroteo con 3 heridos: uno está consciente y camina, otro está inconsciente pero respira, y el tercero no respira. ¿A quién atiendes primero?</div></div>
      <div class="choices">
        <div class="choice-option"><input type="radio" name="q15" id="q15a" value="A"><label for="q15a">A) Al que está caminando, porque es el más fácil</label></div>
        <div class="choice-option"><input type="radio" name="q15" id="q15b" value="B"><label for="q15b">B) Al que no respira — intentar reanimarlo es la prioridad más alta</label></div>
        <div class="choice-option"><input type="radio" name="q15" id="q15c" value="C"><label for="q15c">C) Al inconsciente que respira, porque necesita ser vigilado</label></div>
        <div class="choice-option"><input type="radio" name="q15" id="q15d" value="D"><label for="q15d">D) A los tres al mismo tiempo</label></div>
      </div>
      <div class="answer-area"><p>Comentario opcional:</p><textarea name="q15_exp" placeholder="Tu comentario..."></textarea></div>
    </div>

    <div class="divider"></div>
    <div class="submit-wrap">
      <button type="submit" class="btn-submit" id="btn-submit">✚ Enviar Examen</button>
      <p class="note-sm" style="margin-top:14px">Al enviar confirmas que las respuestas son propias y fueron completadas honestamente.</p>
    </div>
  </form>

  <div id="success">
    <span class="success-icon">✚</span>
    <h2>¡Examen Enviado!</h2>
    <p>Tu examen fue recibido correctamente. El equipo de LimiteRP EMS revisará tus respuestas y te notificará el resultado. Recuerda que aprobar el examen no es definitivo — el siguiente paso es una entrevista con el Jefe de EMS. ¡Buena suerte!</p>
  </div>
</div>

<!-- ═══════════════════════════════════════════
     ADMIN PANEL
════════════════════════════════════════════ -->
<div id="admin-panel">
  <div class="admin-topbar">
    <div class="admin-topbar-left">
      <span class="admin-logo">⚕ EMS <span>Admin</span> — LimiteRP</span>
    </div>
    <div class="admin-topbar-right">
      <button class="btn-sm accent" onclick="openSetupModal()">⚙ Configurar Link</button>
      <button class="btn-sm" onclick="exportCSV()">⬇ Exportar CSV</button>
      <button class="btn-sm danger" onclick="clearAll()">🗑 Limpiar todo</button>
      <button class="btn-sm" onclick="exitAdmin()">← Salir</button>
    </div>
  </div>

  <div class="admin-body">

    <!-- Share banner -->
    <div class="share-banner" id="share-banner">
      <span class="share-icon">🔗</span>
      <div class="share-banner-text">
        <h4>Link del examen para compartir</h4>
        <p>Copia este link y compártelo con los candidatos. <span style="color:var(--accent)">Nota: guarda el HTML en Google Drive o usa GitHub Pages para un link permanente.</span></p>
        <div class="share-url-box">
          <input type="text" class="share-url-input" id="share-url-display" readonly placeholder="Configura el link en ⚙ Configurar Link">
          <button class="btn-copy" id="btn-copy-url" onclick="copyShareUrl()">Copiar</button>
        </div>
      </div>
    </div>

    <!-- Stats -->
    <div class="stat-row">
      <div class="stat-box"><div class="stat-num" id="st-total">0</div><div class="stat-lbl">Total</div></div>
      <div class="stat-box"><div class="stat-num" style="color:var(--green)" id="st-pass">0</div><div class="stat-lbl">Aprobados</div></div>
      <div class="stat-box"><div class="stat-num" style="color:var(--red)" id="st-fail">0</div><div class="stat-lbl">No Aprobados</div></div>
      <div class="stat-box"><div class="stat-num" style="color:var(--accent)" id="st-pend">0</div><div class="stat-lbl">Pendientes</div></div>
      <div class="stat-box"><div class="stat-num" style="color:var(--blue)" id="st-avg">—</div><div class="stat-lbl">Promedio</div></div>
    </div>

    <!-- Filter bar -->
    <div class="filter-bar">
      <input type="text" id="filter-search" placeholder="🔍 Buscar por nombre..." oninput="renderAdmin()">
      <select id="filter-status" onchange="renderAdmin()">
        <option value="">Todos los estados</option>
        <option value="pending">Pendiente</option>
        <option value="pass">Aprobado</option>
        <option value="fail">No Aprobado</option>
      </select>
      <select id="filter-sort" onchange="renderAdmin()">
        <option value="newest">Más reciente primero</option>
        <option value="oldest">Más antiguo primero</option>
        <option value="score-high">Mayor puntaje</option>
        <option value="score-low">Menor puntaje</option>
      </select>
      <span class="filter-count" id="filter-count"></span>
    </div>

    <div id="exam-list"></div>
  </div>
</div>

<!-- Admin trigger -->
<div id="admin-lock">
  <button class="btn-admin-trigger" onclick="openAdminModal()">⚙ Admin</button>
</div>

<!-- Admin login modal -->
<div class="modal-overlay" id="admin-modal">
  <div class="modal-box">
    <h3>Acceso Admin</h3>
    <p>Ingresa la contraseña para acceder al panel.</p>
    <input type="password" id="admin-pw" class="modal-pw" placeholder="Contraseña" style="width:100%;margin-bottom:6px" onkeydown="if(event.key==='Enter')checkAdmin()">
    <span class="modal-err" id="pw-error"></span>
    <button class="btn-modal-ok" onclick="checkAdmin()">INGRESAR</button>
    <button class="btn-modal-cancel" onclick="closeModal('admin-modal')">Cancelar</button>
  </div>
</div>

<!-- Setup / share link modal -->
<div class="setup-modal" id="setup-modal">
  <div class="setup-box">
    <h3>⚙ Configurar Link Compartible</h3>
    <p>Como el examen es un archivo HTML local, aquí hay 3 formas de compartirlo como link real. Elige la más fácil para ti:</p>

    <div class="setup-step">
      <h4>🟢 Opción 1 — GitHub Pages (Gratis, recomendado)</h4>
      <p>1. Crea una cuenta en <a href="https://github.com" target="_blank">github.com</a><br>
      2. Crea un repositorio nuevo (público)<br>
      3. Sube el archivo <code>examen-ems-limiterp.html</code> renombrándolo a <code>index.html</code><br>
      4. Ve a <code>Settings → Pages → Source: main branch</code> y guarda<br>
      5. Tu link será: <code>https://TUUSUARIO.github.io/TUREPO/</code></p>
    </div>

    <div class="setup-step">
      <h4>🔵 Opción 2 — Google Drive</h4>
      <p>1. Sube el HTML a Google Drive<br>
      2. Click derecho → Compartir → "Cualquiera con el link"<br>
      3. Copia el link. <strong>Nota:</strong> Google Drive no renderiza HTML — usa <a href="https://sites.google.com" target="_blank">Google Sites</a> para incrustarlo o pega el link del Drive directo.</p>
    </div>

    <div class="setup-step">
      <h4>🟡 Opción 3 — Pegar el link manualmente aquí</h4>
      <p>Si ya subiste el archivo a GitHub Pages u otro hosting, pega el link aquí para que aparezca en el panel:</p>
      <input type="text" id="custom-share-url" placeholder="https://tuusuario.github.io/ems-limiterp/" style="font-size:13px;margin-top:4px">
    </div>

    <button class="btn-setup-save" onclick="saveShareUrl()">GUARDAR LINK</button>
    <br><br>
    <button class="btn-modal-cancel" onclick="closeModal('setup-modal')">Cerrar</button>
  </div>
</div>

<!-- ═══════════════════════════════════════════
     SCRIPT
════════════════════════════════════════════ -->
<script>
// ── CONFIG ──────────────────────────────────────────────────────────────────
const ADMIN_PW   = "admin123@";
const STORE_KEY  = "limiterp_ems_v3";
const URL_KEY    = "limiterp_share_url";

// Correct answers
const CORRECT = {q1:'B',q2:'B',q3:'B',q4:'C',q5:'A',q6:'B',q7:'B',q8:'B',q9:'B',q10:'B',q11:'B',q12:'B',q13:'B',q14:'B',q15:'B'};

const Q_META = [
  {k:'q1',  t:'¿Qué haces primero al llegar a persona que no responde?'},
  {k:'q2',  t:'Control de sangrado: herida de bala en el brazo'},
  {k:'q3',  t:'Posición de paciente inconsciente que respira'},
  {k:'q4',  t:'¿Qué incluye el RCP básico?'},
  {k:'q5',  t:'Dolor de cuello tras accidente: ¿qué evitas?'},
  {k:'q6',  t:'Persona convulsionando en la calle'},
  {k:'q7',  t:'Primer cuidado ante una quemadura'},
  {k:'q8',  t:'¿Puedes revelar el estado del paciente sin su permiso?'},
  {k:'q9',  t:'¿Qué significa estar "en shock" por sangrado?'},
  {k:'q10', t:'Paciente pregunta si estará bien — respuesta correcta'},
  {k:'q11', t:'¿Atiendes a un criminal conocido?'},
  {k:'q12', t:'Persona atrapada en vehículo — ¿qué haces?'},
  {k:'q13', t:'Labios morados + dolor de pecho + falta de aire'},
  {k:'q14', t:'¿Qué haces al terminar de atender antes de irte?'},
  {k:'q15', t:'Triage: 3 heridos en tiroteo — ¿a quién atiendes primero?'},
];

const OPT_TEXT = {
  q1: {A:'Revisar heridas directamente',B:'Asegurarte del área segura y verificar respiración',C:'Darle agua y esperar',D:'Llamar policía y esperar'},
  q2: {A:'Limpiar con agua primero',B:'Presionar con trapo/venda para detener la sangre',C:'Subir las piernas al aire',D:'Llevarlo al hospital sin hacer nada'},
  q3: {A:'Sentada con espalda recta',B:'De lado — posición de recuperación',C:'Boca arriba con brazos extendidos',D:'De pie apoyada'},
  q4: {A:'Solo respiraciones de boca a boca',B:'Solo compresiones en el pecho',C:'Compresiones + respiraciones (o solo compresiones si estás solo)',D:'Agitar a la persona'},
  q5: {A:'Moverle el cuello/cabeza sin necesidad',B:'Hablarle para calmarlo',C:'Revisar signos vitales',D:'Pedir apoyo por radio'},
  q6: {A:'Sujetarle los brazos',B:'Alejar objetos, poner de lado y esperar',C:'Meterle algo en la boca',D:'Darle agua inmediatamente'},
  q7: {A:'Poner hielo directo',B:'Enfriar con agua fría (no helada)',C:'Pinchar las ampollas',D:'Cubrir con venda muy apretada'},
  q8: {A:'Sí, si la persona lo pide',B:'No, la info del paciente es confidencial',C:'Sí, para que todos estén informados',D:'Solo si es amigo del paciente'},
  q9: {A:'Está muy asustada emocionalmente',B:'Cuerpo sin suficiente sangre para funcionar — emergencia grave',C:'Necesita comer algo',D:'Ya se está recuperando'},
  q10:{A:'"Vas a estar perfectamente bien"',B:'"Estamos haciendo todo lo posible, quédate tranquilo"',C:'"No sé nada, espera"',D:'Ignorarlo y seguir trabajando'},
  q11:{A:'Negarse a atenderlo',B:'Atenderlo igual — el EMS atiende a todos',C:'Llamar policía primero',D:'Solo si la policía está presente'},
  q12:{A:'Jalarlo fuerte para sacarlo',B:'Calmarlo, controlar sangrado y esperar apoyo',C:'Dejarlo solo',D:'Darle medicamentos sin saber qué tiene'},
  q13:{A:'Que tiene hambre',B:'Problema cardíaco o respiratorio grave',C:'Está actuando',D:'Se deshidrató por correr'},
  q14:{A:'Irte de inmediato',B:'Confirmar por radio, verificar estabilidad y hacer reporte',C:'Esperar visto bueno de la policía',D:'No es necesario hacer nada más'},
  q15:{A:'Al que camina — más fácil',B:'Al que no respira — prioridad máxima',C:'Al inconsciente que respira',D:'A los tres al mismo tiempo'},
};

// ── STORAGE ─────────────────────────────────────────────────────────────────
function getAll()  { try{return JSON.parse(localStorage.getItem(STORE_KEY)||'[]')}catch{return[]} }
function saveAll(d){ localStorage.setItem(STORE_KEY,JSON.stringify(d)) }
function addEntry(e){ const l=getAll();l.push(e);saveAll(l) }
function updateEntry(id,patch){
  const l=getAll(); const i=l.findIndex(x=>x.id===id);
  if(i<0)return; Object.assign(l[i],patch); saveAll(l); renderAdmin();
}

function calcScore(ans){ return Object.keys(CORRECT).reduce((s,k)=>s+(ans[k]&&ans[k].choice===CORRECT[k]?1:0),0) }

// ── FORM SUBMIT ──────────────────────────────────────────────────────────────
document.getElementById('exam-form').addEventListener('submit',function(e){
  e.preventDefault();
  const btn=document.getElementById('btn-submit');
  btn.disabled=true; btn.textContent='Enviando...';
  const fd=new FormData(this);
  const ans={};
  Q_META.forEach(q=>{ ans[q.k]={choice:fd.get(q.k)||'—',exp:fd.get(q.k+'_exp')||''} });
  const entry={
    id:Date.now(),
    ts:new Date().toLocaleString('es-ES'),
    name:fd.get('name'), phone:fd.get('phone'), date:fd.get('date'),
    exp:fd.get('experience')||'No especificado', bio:fd.get('bio'),
    answers:ans, result:'pending', resultNote:'', adminNote:''
  };
  addEntry(entry);
  document.getElementById('exam-form').style.display='none';
  document.getElementById('success').style.display='block';
  document.querySelectorAll('#exam-container .section-label').forEach(el=>el.style.display='none');
});

// ── ADMIN AUTH ───────────────────────────────────────────────────────────────
function openAdminModal(){ document.getElementById('admin-modal').classList.add('open'); document.getElementById('admin-pw').value=''; document.getElementById('pw-error').textContent=''; setTimeout(()=>document.getElementById('admin-pw').focus(),80) }
function closeModal(id){ document.getElementById(id).classList.remove('open') }
function checkAdmin(){
  if(document.getElementById('admin-pw').value===ADMIN_PW){ closeModal('admin-modal'); showAdmin(); }
  else{ document.getElementById('pw-error').textContent='Contraseña incorrecta.'; document.getElementById('admin-pw').value=''; document.getElementById('admin-pw').focus(); }
}
function showAdmin(){
  document.getElementById('exam-container').style.display='none';
  document.getElementById('admin-lock').style.display='none';
  document.getElementById('admin-panel').style.display='block';
  renderAdmin();
  // Load share url
  const url=localStorage.getItem(URL_KEY)||'';
  if(url) document.getElementById('share-url-display').value=url;
}
function exitAdmin(){
  document.getElementById('admin-panel').style.display='none';
  document.getElementById('exam-container').style.display='block';
  document.getElementById('admin-lock').style.display='block';
}

// ── SETUP MODAL ──────────────────────────────────────────────────────────────
function openSetupModal(){ document.getElementById('setup-modal').classList.add('open'); const u=localStorage.getItem(URL_KEY)||''; document.getElementById('custom-share-url').value=u; }
function saveShareUrl(){
  const u=document.getElementById('custom-share-url').value.trim();
  localStorage.setItem(URL_KEY,u);
  document.getElementById('share-url-display').value=u||'(sin link configurado)';
  closeModal('setup-modal');
}
function copyShareUrl(){
  const u=document.getElementById('share-url-display').value;
  if(!u||u==='(sin link configurado)'){ alert('Configura primero el link en ⚙ Configurar Link'); return; }
  navigator.clipboard.writeText(u).then(()=>{
    const b=document.getElementById('btn-copy-url');
    b.textContent='¡Copiado!'; b.classList.add('copied');
    setTimeout(()=>{ b.textContent='Copiar'; b.classList.remove('copied'); },2000);
  });
}

// ── RENDER ADMIN ─────────────────────────────────────────────────────────────
function renderAdmin(){
  let list=getAll();
  // Stats
  const total=list.length, passes=list.filter(x=>x.result==='pass').length, fails=list.filter(x=>x.result==='fail').length, pend=list.filter(x=>x.result==='pending').length;
  const scores=list.map(x=>calcScore(x.answers));
  const avg=total?Math.round(scores.reduce((a,b)=>a+b,0)/total*10)/10:'—';
  document.getElementById('st-total').textContent=total;
  document.getElementById('st-pass').textContent=passes;
  document.getElementById('st-fail').textContent=fails;
  document.getElementById('st-pend').textContent=pend;
  document.getElementById('st-avg').textContent=avg;
  // Filter
  const search=(document.getElementById('filter-search').value||'').toLowerCase();
  const status=document.getElementById('filter-status').value;
  const sort=document.getElementById('filter-sort').value;
  let filtered=list.filter(x=>{
    if(search && !x.name.toLowerCase().includes(search)) return false;
    if(status && x.result!==status) return false;
    return true;
  });
  if(sort==='oldest') filtered.sort((a,b)=>a.id-b.id);
  else if(sort==='newest') filtered.sort((a,b)=>b.id-a.id);
  else if(sort==='score-high') filtered.sort((a,b)=>calcScore(b.answers)-calcScore(a.answers));
  else if(sort==='score-low') filtered.sort((a,b)=>calcScore(a.answers)-calcScore(b.answers));
  else filtered.sort((a,b)=>b.id-a.id);
  document.getElementById('filter-count').textContent=`${filtered.length} resultado(s)`;
  const el=document.getElementById('exam-list');
  if(filtered.length===0){ el.innerHTML=`<div class="empty-state"><div class="big">📋</div><p>${total===0?'Aún no hay exámenes recibidos.':'Ningún examen coincide con los filtros.'}</p></div>`; return; }
  el.innerHTML='';
  filtered.forEach(r=>{ el.appendChild(buildCard(r)); });
}

function buildCard(r){
  const score=calcScore(r.answers);
  const pct=Math.round(score/15*100);
  const passing=pct>=70;
  // Status badge
  const badge=r.result==='pass'?`<span class="badge badge-pass">✓ Aprobado</span>`:r.result==='fail'?`<span class="badge badge-fail">✗ No Aprobado</span>`:`<span class="badge badge-pending">⏳ Pendiente</span>`;
  // Score pill
  const pill=`<span class="score-pill ${passing?'score-good':'score-bad'}">${score}/15</span>`;
  const div=document.createElement('div');
  div.className='exam-card';
  div.innerHTML=`
    <div class="exam-header" onclick="toggleCard(${r.id})">
      <div style="flex:1;min-width:0">
        <div style="display:flex;align-items:center;gap:8px;flex-wrap:wrap">
          <span class="exam-name">✚ ${esc(r.name)}</span>
          ${badge} ${pill}
        </div>
        <div class="exam-meta-row">
          <span>📞 ${esc(r.phone)}</span>
          <span>📅 ${esc(r.date)}</span>
          <span>Exp: ${esc(r.exp)}</span>
          <span style="font-size:11px">Enviado: ${esc(r.ts)}</span>
        </div>
      </div>
      <span class="exam-toggle" id="tog-${r.id}">▼</span>
    </div>
    <div class="exam-body" id="body-${r.id}">
      ${buildBody(r,score,pct,passing)}
    </div>`;
  return div;
}

function buildBody(r,score,pct,passing){
  // Info grid
  const info=`<div class="info-grid">
    <div class="info-item"><label>Nombre</label><span>${esc(r.name)}</span></div>
    <div class="info-item"><label>Teléfono</label><span>${esc(r.phone)}</span></div>
    <div class="info-item"><label>Fecha</label><span>${esc(r.date)}</span></div>
    <div class="info-item"><label>Experiencia previa</label><span>${esc(r.exp)}</span></div>
  </div>
  <div style="margin-bottom:16px;padding-bottom:16px;border-bottom:1px solid var(--border)">
    <div style="font-size:10px;font-weight:700;letter-spacing:.1em;color:var(--red);text-transform:uppercase;margin-bottom:4px">Motivación</div>
    <div style="font-size:13px;color:var(--text-muted);font-style:italic">${esc(r.bio)}</div>
  </div>`;

  // Score bar
  const scoreBar=`<div class="score-overview">
    <div>
      <div style="font-size:11px;color:var(--text-muted);text-transform:uppercase;letter-spacing:.1em;margin-bottom:2px">Puntaje</div>
      <span class="score-big ${passing?'score-good':'score-bad'}">${score}/15</span>
    </div>
    <div class="score-bar-wrap">
      <div class="score-bar-bg"><div class="score-bar-fill ${passing?'good':'bad'}" style="width:${pct}%"></div></div>
      <div style="display:flex;justify-content:space-between;font-size:11px;color:var(--text-muted)">
        <span>${pct}% — ${passing?'≥70% alcanzado':'Por debajo del 70%'}</span>
        <span>✓${score} &nbsp; ✗${15-score}</span>
      </div>
    </div>
  </div>`;

  // Answers
  let qrows='';
  Q_META.forEach((q,i)=>{
    const ans=r.answers[q.k]||{};
    const chosen=ans.choice||'—';
    const correct=CORRECT[q.k];
    const isOk=chosen===correct;
    const mark=chosen==='—'?'<span style="color:var(--text-muted);font-size:15px">—</span>':isOk?'<span class="ans-mark">✅</span>':'<span class="ans-mark">❌</span>';
    const chosenLabel=chosen==='—'?'No respondió':`${chosen}) ${OPT_TEXT[q.k]&&OPT_TEXT[q.k][chosen]?OPT_TEXT[q.k][chosen]:chosen}`;
    const correctRow=!isOk&&chosen!=='—'?`<div class="ans-correct-row">✓ Correcta: ${correct}) ${OPT_TEXT[q.k][correct]||correct}</div>`:'';
    const expRow=ans.exp?`<div class="ans-comment">💬 "${esc(ans.exp)}"</div>`:'';
    qrows+=`<div class="ans-row">
      <div class="ans-qnum">Pregunta ${String(i+1).padStart(2,'0')}</div>
      <div class="ans-qtext">${q.t}</div>
      <div class="ans-chosen">${mark}<div class="ans-box ${chosen==='—'?'':isOk?'correct':'wrong'}">${esc(chosenLabel)}</div></div>
      ${correctRow}${expRow}
    </div>`;
  });

  // Admin note
  const noteHtml=`<div class="admin-notes-area">
    <label>Nota interna del admin (solo visible en el panel):</label>
    <textarea id="anote-${r.id}">${esc(r.adminNote)}</textarea>
    <button class="btn-save-note" onclick="saveAdminNote(${r.id})">💾 Guardar nota</button>
  </div>`;

  // Quick-correct override
  const overrideOpts=Array.from({length:15},(_,i)=>`<option value="${i+1}">Pregunta ${String(i+1).padStart(2,'0')}</option>`).join('');
  const overrideHtml=`<div class="quick-tool">
    <h5>🔧 Herramienta de corrección manual</h5>
    <div class="quick-tool-row">
      <select id="ov-q-${r.id}" class="override-select">${overrideOpts}</select>
      <select id="ov-a-${r.id}" class="override-select"><option value="A">A</option><option value="B">B</option><option value="C">C</option><option value="D">D</option></select>
      <button class="btn-override" onclick="applyOverride(${r.id})">Aplicar corrección</button>
    </div>
    <p class="override-note">Úsalo si necesitas corregir manualmente la respuesta elegida por el candidato en una pregunta específica.</p>
  </div>`;

  // Result sender
  const noteVal=r.resultNote||'';
  const sentBox=r.result!=='pending'?`<div class="result-sent-box ${r.result} show">
    ${r.result==='pass'?'✓ Marcado como APROBADO PROVISIONAL':'✗ Marcado como NO APROBADO PROVISIONAL'}
    ${noteVal?` — Nota: "${esc(noteVal)}"`:''}<br>
    <span style="font-size:11px;opacity:.75">Resultado no definitivo — el candidato debe pasar entrevista con el Jefe de EMS.</span>
  </div>`:'<div class="result-sent-box" id="rsent-'+r.id+'"></div>';

  const resultPanel=`<div class="result-panel">
    <h4>📨 Enviar Resultado al Candidato</h4>
    <p>El resultado es provisional. El candidato aún debe pasar la entrevista con el Jefe de EMS.</p>
    <textarea class="result-note-box" id="rnote-${r.id}" placeholder="Nota para el candidato (opcional)...">${esc(noteVal)}</textarea>
    <div class="result-btn-row">
      <button class="btn-approve" onclick="setResult(${r.id},'pass')">✓ Marcar APROBADO</button>
      <button class="btn-reject" onclick="setResult(${r.id},'fail')">✗ Marcar NO APROBADO</button>
      ${r.result!=='pending'?`<button class="btn-reset-res" onclick="setResult(${r.id},'pending')">↺ Resetear</button>`:''}
    </div>
    ${sentBox}
  </div>`;

  return `${info}${scoreBar}
    <div class="answers-section"><h4>Respuestas del candidato</h4>${qrows}</div>
    ${overrideHtml}${noteHtml}${resultPanel}`;
}

function toggleCard(id){
  const body=document.getElementById('body-'+id);
  const tog=document.getElementById('tog-'+id);
  if(body.classList.contains('open')){ body.classList.remove('open'); tog.textContent='▼'; }
  else{ body.classList.add('open'); tog.textContent='▲'; }
}

// ── ACTIONS ──────────────────────────────────────────────────────────────────
function setResult(id,result){
  if(result!=='pending'&&!confirm(`¿Marcar como "${result==='pass'?'APROBADO':'NO APROBADO'}"?`))return;
  const note=document.getElementById('rnote-'+id)?.value||'';
  updateEntry(id,{result,resultNote:note});
}

function saveAdminNote(id){
  const note=document.getElementById('anote-'+id)?.value||'';
  updateEntry(id,{adminNote:note});
  const btn=event.target; btn.textContent='✓ Guardado'; setTimeout(()=>btn.textContent='💾 Guardar nota',1500);
}

function applyOverride(id){
  const qNum=parseInt(document.getElementById('ov-q-'+id).value);
  const newAns=document.getElementById('ov-a-'+id).value;
  const k='q'+qNum;
  const list=getAll(); const i=list.findIndex(x=>x.id===id); if(i<0)return;
  if(!list[i].answers[k]) list[i].answers[k]={choice:'—',exp:''};
  list[i].answers[k].choice=newAns;
  saveAll(list);
  renderAdmin();
  alert(`Pregunta ${String(qNum).padStart(2,'0')} corregida a opción ${newAns}.`);
}

function clearAll(){
  if(!confirm('¿Borrar TODOS los exámenes? No se puede deshacer.'))return;
  localStorage.removeItem(STORE_KEY); renderAdmin();
}

function exportCSV(){
  const list=getAll();
  if(!list.length){ alert('No hay exámenes para exportar.'); return; }
  const headers=['ID','Fecha','Nombre','Teléfono','Experiencia','Puntaje','%','Resultado','Nota Admin'];
  const rows=list.map(r=>{
    const s=calcScore(r.answers);
    return [r.id,r.ts,r.name,r.phone,r.exp,s,Math.round(s/15*100)+'%',r.result,r.adminNote||''].map(v=>`"${String(v).replace(/"/g,'""')}"`).join(',');
  });
  const csv=[headers.join(','),...rows].join('\n');
  const a=document.createElement('a');
  a.href='data:text/csv;charset=utf-8,'+encodeURIComponent(csv);
  a.download='examenes-ems-limiterp.csv';
  a.click();
}

function esc(s){ if(!s)return'—'; return String(s).replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;').replace(/"/g,'&quot;').replace(/\n/g,'<br>') }

// Init
document.getElementById('f-date').value=new Date().toISOString().split('T')[0];
const _savedUrl=localStorage.getItem(URL_KEY)||'';
if(_savedUrl) document.getElementById('share-url-display').value=_savedUrl;
</script>
</body>
</html>
