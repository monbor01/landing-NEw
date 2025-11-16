<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Exclusive Gift — Limited Time Offer</title>
  <meta name="description" content="Claim your exclusive gift — limited time. Click anywhere to claim.">
  <style>
    /* Inline CSS - single file, responsive, minimalistic, high-contrast */
    :root{
      --bg:#071026;
      --card:#0b2340;
      --accent:#00d1b2;
      --accent-2:#00b0ff;
      --text:#f7fbff;
      --muted:#9fb0c8;
      --danger:#ff6b6b;
      --shadow: 0 10px 30px rgba(2,8,23,0.6);
      --radius:18px;
      --maxw:860px;
      --cta-size:clamp(48px,7vw,64px);
      --gap:18px;
      font-family: Inter, ui-sans-serif, system-ui, -apple-system, "Segoe UI", Roboto, "Helvetica Neue", Arial;
    }
    html,body{height:100%}
    body{
      margin:0;
      background:
        radial-gradient(1200px 600px at 10% 10%, rgba(0,208,178,0.06), transparent 6%),
        radial-gradient(1000px 500px at 90% 90%, rgba(0,176,255,0.05), transparent 8%),
        var(--bg);
      color:var(--text);
      -webkit-font-smoothing:antialiased;
      -moz-osx-font-smoothing:grayscale;
      display:flex;
      align-items:center;
      justify-content:center;
      padding:28px;
    }

    .container{
      width:100%;
      max-width:var(--maxw);
      background:linear-gradient(180deg, rgba(255,255,255,0.02), rgba(255,255,255,0.01));
      border-radius:calc(var(--radius) + 6px);
      box-shadow:var(--shadow);
      overflow:hidden;
      position:relative;
      border:1px solid rgba(255,255,255,0.03);
    }

    .hero{
      display:grid;
      grid-template-columns:1fr;
      gap:var(--gap);
      padding:40px;
      align-items:center;
      text-align:center;
    }

    .top-row{
      display:flex;
      justify-content:space-between;
      align-items:center;
      gap:12px;
    }

    #timer{
      background:linear-gradient(90deg, rgba(255,255,255,0.03), rgba(255,255,255,0.02));
      border-radius:12px;
      padding:8px 14px;
      font-weight:600;
      letter-spacing:0.6px;
      color:var(--text);
      display:inline-flex;
      align-items:center;
      gap:8px;
      user-select:none;
      cursor:default;
      box-shadow: 0 4px 14px rgba(0,0,0,0.45) inset;
      border:1px solid rgba(255,255,255,0.03);
    }

    .headline{
      font-size:clamp(22px,3.8vw,34px);
      margin:6px 0 8px 0;
      font-weight:700;
      letter-spacing:-0.4px;
      line-height:1.06;
      color:var(--text);
    }

    .sub{
      color:var(--muted);
      font-size:clamp(14px,2vw,16px);
      margin-bottom:18px;
    }

    .card{
      background:linear-gradient(180deg, rgba(255,255,255,0.02), rgba(255,255,255,0.01));
      border-radius:14px;
      padding:28px;
      display:flex;
      gap:20px;
      align-items:center;
      justify-content:center;
      flex-direction:column;
    }

    .cta{
      display:inline-flex;
      align-items:center;
      justify-content:center;
      padding:0 28px;
      height:var(--cta-size);
      min-width:clamp(240px,50%,320px);
      font-size:clamp(18px,2.6vw,22px);
      font-weight:800;
      border-radius:12px;
      background:linear-gradient(90deg,var(--accent),var(--accent-2));
      color:#022029;
      text-decoration:none;
      box-shadow: 0 14px 40px rgba(0,208,178,0.12), 0 6px 14px rgba(0,176,255,0.08);
      transition:transform .14s ease, box-shadow .14s ease;
      cursor:pointer;
      user-select:none;
      border:0;
    }

    .cta:active{transform:translateY(2px) scale(.997)}
    .cta:hover{transform:translateY(-6px)}

    .small{
      font-size:13px;
      color:var(--muted);
      margin-top:12px;
      max-width:720px;
    }

    .trust{
      margin-top:18px;
      display:flex;
      gap:12px;
      align-items:center;
      justify-content:center;
      flex-wrap:wrap;
      color:var(--muted);
      font-size:13px;
    }

    .badge{
      background:rgba(255,255,255,0.02);
      padding:8px 12px;
      border-radius:999px;
      border:1px solid rgba(255,255,255,0.02);
      display:inline-flex;
      gap:8px;
      align-items:center;
      font-weight:600;
    }

    .accent-text{ color:var(--accent); font-weight:800; }

    /* footer */
    .footer{
      text-align:center;
      padding:18px 22px;
      border-top:1px solid rgba(255,255,255,0.02);
      color:var(--muted);
      font-size:13px;
      display:flex;
      justify-content:space-between;
      gap:12px;
      align-items:center;
    }

    @media (min-width:880px){
      .hero{ padding:44px 56px; grid-template-columns:1fr; text-align:left; }
      .hero .center{ align-items:center; display:flex; flex-direction:column; text-align:center; }
      .headline{ font-size:44px; text-align:center; }
      .sub{ text-align:center; }
      .card{ flex-direction:column; }
      .footer{ padding:18px 44px; }
    }

    /* subtle pulse around CTA to draw attention */
    .pulse{
      position:absolute;
      left:50%;
      top:50%;
      transform:translate(-50%,-50%);
      width:calc(var(--cta-size) + 160px);
      height:calc(var(--cta-size) + 160px);
      border-radius:50%;
      pointer-events:none;
      opacity:0.06;
      filter:blur(28px);
      mix-blend-mode:screen;
      background:radial-gradient(circle at center, var(--accent), transparent 45%);
    }

    /* visually-hidden for accessibility if needed */
    .sr-only{ position:absolute !important; height:1px; width:1px; overflow:hidden; clip:rect(1px,1px,1px,1px); white-space:nowrap; }
  </style>
</head>
<body>
  <div class="container" id="page-root" role="document" aria-label="Limited time gift offer">
    <div class="hero">
      <div class="top-row" style="justify-content:center;">
        <!-- Timer (must remain visible and functional; clicking it will NOT redirect) -->
        <div id="timer" aria-live="polite" title="Offer countdown" role="status">
          ⏳ Time left:
          <strong id="countdown" style="font-variant-numeric:tabular-nums; margin-left:6px;">05:00:00</strong>
        </div>
      </div>

      <div style="display:flex;flex-direction:column;align-items:center;gap:12px;">
        <h1 class="headline">Claim Your Exclusive Gift — Only for a Few Hours</h1>
        <p class="sub">A limited-time bonus to help you get faster results. Honestly presented — no spam. Click now to unlock your gift.</p>
      </div>

      <div class="card" aria-hidden="false">
        <div style="max-width:720px; text-align:center;">
          <p style="font-size:15px; color:var(--muted); margin:0 0 18px 0;">
            This exclusive gift has been reserved just for visitors like you. It contains high-value resources and actionable tips used by top performers. The offer is time-limited — don't miss it.
          </p>
        </div>

        <!-- CTA central button; clicking it redirects -->
        <button id="cta" class="cta" role="link" aria-label="Claim Your Exclusive Gift Now">
          Claim Your Exclusive Gift Now
        </button>

        <div class="small">No credit card required • Instant access after click • Secure link</div>

        <div class="trust" aria-hidden="true">
          <div class="badge">✔ Trusted by thousands</div>
          <div class="badge">⚡ Instant delivery</div>
          <div class="badge">🔒 Secure link</div>
        </div>
      </div>
    </div>

    <div class="footer" style="gap:12px;">
      <div>Limited-time offer • Act fast</div>
      <div style="text-align:right;">Questions? <span style="color:var(--muted)">Support available</span></div>
    </div>

    <!-- Decorative pulse (non-interactive) -->
    <div class="pulse" aria-hidden="true"></div>
  </div>

  <script>
    /*
      Single-file HTML with inline JS.
      Behavior:
        - 5-hour countdown from page load (displayed in #countdown)
        - When countdown reaches zero: shows "Offer Expired!" text (but page clicks STILL redirect)
        - Any click anywhere on the page redirects to the provided link, EXCEPT clicks directly on the timer element (#timer)
        - The CTA button also redirects (as required) and is prominent
    */

    (function(){
      // === Configuration ===
      var targetUrl = "https://www.effectivegatecpm.com/qit8cdgic?key=78ea178d953e4cd9325fd331849e9bbc";
      var FIVE_HOURS_MS = 5 * 60 * 60 * 1000;

      // === Countdown setup ===
      var countdownEl = document.getElementById('countdown');
      var timerRoot = document.getElementById('timer');

      // Create an absolute expiry time 5 hours from now.
      // (Using client time; if you need server-based expiry, replace with server timestamp.)
      var expiry = Date.now() + FIVE_HOURS_MS;

      function formatTime(ms){
        if (ms <= 0) return "00:00:00";
        var s = Math.floor(ms / 1000);
        var hours = Math.floor(s / 3600); s %= 3600;
        var minutes = Math.floor(s / 60);
        var seconds = s % 60;
        function pad(n){ return String(n).padStart(2,'0'); }
        return pad(hours) + ":" + pad(minutes) + ":" + pad(seconds);
      }

      function tick(){
        var remaining = expiry - Date.now();
        if (remaining <= 0){
          countdownEl.textContent = "Offer Expired!";
          countdownEl.style.color = "";
          // Keep ticking to show final state as expired (and keep it visible)
          return;
        }
        countdownEl.textContent = formatTime(remaining);
      }

      // Update every 250ms for snappy seconds
      tick();
      var interval = setInterval(tick, 250);

      // === Redirect-on-click behavior ===
      // Any click anywhere on the document redirects to targetUrl.
      // But we must NOT redirect when the user clicks on the timer (so it's visible and interactive)
      // We'll also avoid redirecting when clicking elements with data-no-redirect attribute (if needed).
      function shouldBypassRedirect(el){
        if (!el) return false;
        if (el.id === 'timer') return true;
        if (el.closest && el.closest('#timer')) return true;
        // allow adding attribute data-no-redirect to any element to opt-out
        if (el.closest && el.closest('[data-no-redirect]')) return true;
        return false;
      }

      // Attach a single listener that captures clicks early to maximize coverage.
      document.addEventListener('click', function(e){
        // If user clicked timer area or children, do not redirect
        if (shouldBypassRedirect(e.target)) {
          // allow default timer interactions (none here), but prevent propagation to global redirect
          e.stopPropagation();
          return;
        }

        // For accessibility: only follow redirect for primary mouse button or keyboard activation
        // (still allow middle-click / ctrl+click to behave naturally by not preventing default)
        // We'll use location.assign for a first-party redirect experience.
        try {
          // If user used meta/ctrl/shift to open in new tab, respect it by using window.open
          if (e.ctrlKey || e.metaKey || e.shiftKey || e.button === 1) {
            window.open(targetUrl, "_blank");
            return;
          }
        } catch(err){ /* noop */ }

        // Prevent double-handling and redirect immediately.
        e.preventDefault();
        // Provide a quick visual feedback by slightly scaling the clicked element (not required)
        // Then redirect:
        window.location.href = targetUrl;
      }, {capture:true, passive:false});

      // Make CTA behave like a link (also for keyboard users)
      var cta = document.getElementById('cta');
      cta.addEventListener('click', function(e){
        e.preventDefault();
        // Respect modifier keys to allow opening in new tab
        if (e.ctrlKey || e.metaKey || e.shiftKey) {
          window.open(targetUrl, "_blank");
          return;
        }
        window.location.href = targetUrl;
      });

      // Keyboard accessibility: Enter or Space on page root should redirect too
      document.addEventListener('keydown', function(e){
        // Avoid redirect when focused in the timer (so screen reader users can interact)
        var active = document.activeElement;
        if (shouldBypassRedirect(active)) return;

        // If user presses Enter or Space and focus is not on an input, redirect.
        if ((e.key === 'Enter' || e.key === ' ') && !/input|textarea|select/i.test(active && active.tagName)) {
          e.preventDefault();
          window.location.href = targetUrl;
        }
      });

      // Make sure timer itself does not cause page redirection when clicked:
      timerRoot.addEventListener('click', function(e){
        e.stopPropagation();
        // Optionally — allow copying remaining time or interacting — do nothing else.
      });

      // Small enhancement: animate CTA pulse subtly (no external assets)
      // and make sure it's visually emphasized for higher CTR.
      (function addPulse(){
        var el = document.querySelector('.pulse');
        if (!el) return;
        var a = 0;
        setInterval(function(){
          a += 0.03;
          el.style.opacity = (0.04 + 0.02 * Math.sin(a)).toString();
        }, 60);
      })();

      // On visibility change, re-sync expiry so user switching tabs sees correct remaining time
      document.addEventListener('visibilitychange', function(){
        tick();
      });

      // Clean up when needed (not required in single-page file but good practice)
      window.addEventListener('unload', function(){
        clearInterval(interval);
      });

    })();
  </script>
</body>
</html>
# landing-NEw
landing page avec compte à rebours
