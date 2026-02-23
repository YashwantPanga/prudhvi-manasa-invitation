<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=yes">
    <title>Prudhvi & Manasa · engagement envelope</title>
    <!-- elegant serif + cinematic font -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,400;0,500;0,600;0,700;1,400;1,500;1,600;1,700&family=Playfair+Display:ital,wght@0,400;0,600;0,700;1,500&display=swap" rel="stylesheet">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            user-select: none;
        }

        body {
            background: linear-gradient(145deg, #1f2a1e 0%, #2f3a2c 100%);
            min-height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            font-family: 'Cormorant Garamond', 'Georgia', serif;
            padding: 12px;
            perspective: 1200px;
        }

        /* ===== MAIN WRAPPER ===== */
        .envelope-wrapper {
            max-width: 500px;
            width: 100%;
            position: relative;
            cursor: pointer;
            display: flex;
            flex-direction: column;
            align-items: center;
        }

        /* ----- ENVELOPE – now richly decorated with engagement elements ----- */
        .envelope {
            position: relative;
            width: 100%;
            background: #dbaa7a;
            border-radius: 24px 24px 16px 16px;
            box-shadow: 0 25px 32px -10px rgba(0,0,0,0.6), 0 0 0 2px #f3d2ae, 0 0 0 6px #b58254;
            transition: all 0.7s cubic-bezier(0.34, 1.4, 0.55, 1);
            transform-style: preserve-3d;
            z-index: 10;
            border: 1px solid #efd0b0;
            /* decorative pattern (very subtle) */
            background-image: repeating-linear-gradient(45deg, rgba(255,240,210,0.2) 0px, rgba(255,240,210,0.2) 6px, transparent 6px, transparent 16px);
        }

        .flap {
            position: absolute;
            top: -38px;
            left: 0;
            width: 100%;
            height: 76px;
            background: #cf9f6e;
            border-radius: 40px 40px 0 0;
            box-shadow: 0 -10px 12px rgba(0,0,0,0.2), inset 0 10px 12px #fadbb8;
            transform-origin: bottom;
            transition: transform 0.8s ease 0.15s, opacity 0.3s;
            z-index: 25;
            clip-path: polygon(0% 0%, 100% 0%, 88% 100%, 12% 100%);
            border-bottom: 4px solid #b57a4a;
            /* engagement pattern on flap */
            background-image: radial-gradient(circle at 20% 30%, #f5d2aa 3px, transparent 4px),
                              radial-gradient(circle at 80% 70%, #f5d2aa 3px, transparent 4px);
            background-size: 30px 30px;
        }

        .envelope::after {
            content: '';
            position: absolute;
            bottom: -28px;
            left: 0;
            width: 100%;
            height: 32px;
            background: #c28d5c;
            border-radius: 0 0 40px 40px;
            box-shadow: 0 16px 10px -8px #2f2a24;
            clip-path: polygon(0% 0%, 100% 0%, 92% 100%, 8% 100%);
            z-index: -1;
            transition: opacity 0.3s;
        }

        .envelope.closed .flap {
            transform: rotateX(0deg);
        }
        .envelope.open .flap {
            transform: rotateX(-185deg);
            opacity: 0;
        }

        .envelope.open {
            background: transparent !important;
            box-shadow: none !important;
            border: none !important;
            transition: background 0.2s, box-shadow 0.2s;
        }
        .envelope.open::after {
            opacity: 0;
            transition: opacity 0.2s;
        }
        .envelope.open .flap {
            opacity: 0;
            transition: opacity 0.2s, transform 0.8s;
        }

        /* ----- ENGAGEMENT DECORATIONS ON ENVELOPE (visible only when closed) ----- */
        .envelope-decor {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: 30;
            overflow: hidden;
            border-radius: inherit;
        }

        .envelope.closed .envelope-decor {
            display: block;
        }
        .envelope.open .envelope-decor {
            display: none;
        }

        /* golden rings */
        .ring-decor {
            position: absolute;
            width: 60px;
            height: 60px;
            border: 5px solid #f5cf9c;
            border-radius: 50%;
            box-shadow: 0 0 0 3px #b37b4a, 0 8px 12px rgba(0,0,0,0.3);
            background: radial-gradient(circle at 30% 30%, #fff6e6, transparent 70%);
        }

        .ring-1 {
            top: 30px;
            left: 20px;
            transform: rotate(-15deg);
            width: 55px;
            height: 55px;
        }
        .ring-1::after {
            content: '💍';
            position: absolute;
            font-size: 28px;
            top: -8px;
            left: 8px;
            transform: rotate(25deg);
            filter: drop-shadow(0 4px 4px #a1521a);
        }

        .ring-2 {
            bottom: 30px;
            right: 20px;
            width: 65px;
            height: 65px;
            border-color: #f3c68f;
            transform: rotate(10deg);
        }
        .ring-2::after {
            content: '💍';
            position: absolute;
            font-size: 32px;
            bottom: -8px;
            right: 8px;
            transform: rotate(-15deg);
            filter: drop-shadow(0 4px 4px #9c4a1c);
        }

        /* hearts scatter */
        .heart-decor {
            position: absolute;
            color: #e6835c;
            font-size: 30px;
            filter: drop-shadow(0 4px 6px #6d351a);
            opacity: 0.8;
            animation: heartFloat 3s infinite alternate;
        }

        .heart-1 { top: 15px; right: 35px; font-size: 40px; animation-delay: 0.2s; }
        .heart-2 { bottom: 20px; left: 40px; font-size: 35px; animation-delay: 0.7s; }
        .heart-3 { top: 80px; left: 55px; font-size: 28px; animation-delay: 0.4s; }

        @keyframes heartFloat {
            0% { transform: translateY(0) scale(1); }
            100% { transform: translateY(-6px) scale(1.05); }
        }

        /* engagement banner */
        .banner {
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            background: #fcedd3;
            color: #7b4d2b;
            font-family: 'Playfair Display', serif;
            font-size: 22px;
            font-weight: 700;
            letter-spacing: 4px;
            padding: 8px 22px;
            border-radius: 60px;
            white-space: nowrap;
            box-shadow: 0 8px 0 #a5724b, 0 12px 20px rgba(80,40,10,0.4);
            border: 2px solid #eabb94;
            text-transform: uppercase;
            z-index: 35;
            backdrop-filter: blur(2px);
            animation: bannerGlow 2.2s infinite;
        }

        @keyframes bannerGlow {
            0% { box-shadow: 0 8px 0 #a5724b, 0 12px 20px rgba(80,40,10,0.4); }
            50% { box-shadow: 0 8px 0 #c79464, 0 16px 28px #b45f2a; }
            100% { box-shadow: 0 8px 0 #a5724b, 0 12px 20px rgba(80,40,10,0.4); }
        }

        /* small ring dots */
        .confetti-dot {
            position: absolute;
            width: 8px;
            height: 8px;
            background: #fad37d;
            border-radius: 50%;
            box-shadow: 0 0 10px #f5b576;
        }
        .dot1 { top: 60px; left: 80px; }
        .dot2 { bottom: 70px; right: 70px; }
        .dot3 { top: 110px; right: 40px; }

        /* invitation card */
        .invitation-card {
            position: relative;
            width: 100%;
            background: #fef9f0;
            background-image: radial-gradient(circle at 20% 30%, rgba(255,235,200,0.3) 0%, transparent 30%),
                              repeating-linear-gradient(45deg, rgba(200,170,140,0.1) 0px, rgba(200,170,140,0.1) 2px, transparent 2px, transparent 8px);
            border-radius: 24px 24px 20px 20px;
            box-shadow: 0 25px 35px -8px #2d1f16, 0 0 0 1px #edd7bd, 0 0 0 4px #fbebd2;
            overflow: hidden;
            transition: all 0.8s cubic-bezier(0.2, 1.1, 0.3, 1.1);
            transform: scale(0.7) translateY(90px);
            opacity: 0;
            z-index: 5;
            will-change: transform, opacity;
        }

        .envelope.open .invitation-card {
            transform: scale(1) translateY(0);
            opacity: 1;
            transition-delay: 0.3s;
            animation: zoomInGentle 0.9s ease-out;
        }

        .envelope.closed .invitation-card {
            transform: scale(0.7) translateY(90px);
            opacity: 0;
            pointer-events: none;
        }

        @keyframes zoomInGentle {
            0% { transform: scale(0.7) translateY(90px); }
            40% { transform: scale(1.02) translateY(-2px); }
            100% { transform: scale(1) translateY(0); }
        }

        /* ===== TAP HINT (brown, centered) ===== */
        .tap-hint {
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            color: #5f3e2b;
            font-family: 'Playfair Display', serif;
            font-size: 26px;
            font-weight: 600;
            letter-spacing: 6px;
            text-transform: uppercase;
            white-space: nowrap;
            text-shadow: 0 2px 6px #efcca8, 0 0 0 1px #fbe1c6;
            z-index: 50;
            pointer-events: none;
            opacity: 1;
            transition: opacity 0.5s ease 0.1s;
            background: rgba(240, 215, 180, 0.2);
            padding: 6px 20px;
            border-radius: 60px;
            backdrop-filter: blur(2px);
            border: 1px solid rgba(130, 70, 30, 0.3);
            box-shadow: 0 6px 12px rgba(90, 50, 20, 0.3);
        }

        .envelope.open ~ .tap-hint {
            opacity: 0 !important;
            visibility: hidden !important;
            transition: opacity 0.3s, visibility 0s 0.3s;
        }

        /* ===== NATURAL FLOWER ANIMATIONS IN CORNERS ===== */
        .flower-corner {
            position: absolute;
            width: min(160px, 35vw);
            height: min(160px, 35vw);
            max-width: 180px;
            max-height: 180px;
            pointer-events: none;
            z-index: 25;
            opacity: 0.9;
            background-size: contain;
            background-repeat: no-repeat;
            background-position: center;
            filter: drop-shadow(0 8px 10px rgba(150, 70, 20, 0.35));
            animation: none;
        }

        .corner-tl {
            top: -20px;
            left: -20px;
            background-image: url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 140 140"><g fill="%23d14e2b" opacity="0.95"><circle cx="30" cy="32" r="14" fill="%23f0592b" opacity="0.9"/><circle cx="46" cy="22" r="12" fill="%23f06a39" opacity="0.9"/><circle cx="20" cy="50" r="11" fill="%23e06734" opacity="0.9"/><circle cx="55" cy="45" r="10" fill="%23d85a2a" opacity="0.9"/><circle cx="38" cy="60" r="13" fill="%23f07742" opacity="0.9"/><circle cx="15" cy="27" r="8" fill="%23f59E6d" opacity="0.9"/><circle cx="63" cy="30" r="9" fill="%23e36e36" opacity="0.9"/><circle cx="25" cy="70" r="8" fill="%23ee8a50" opacity="0.8"/><path d="M27 20 Q38 8 47 18" stroke="%236b4a2b" stroke-width="3" fill="none" stroke-opacity="0.7"/><path d="M17 40 Q30 30 44 36" stroke="%236b4a2b" stroke-width="3" fill="none" stroke-opacity="0.7"/><circle cx="40" cy="14" r="5" fill="%239bc35b" opacity="0.8"/></g></svg>');
            animation: bloomNaturalTL 5s infinite ease-in-out;
        }
        .corner-tr {
            top: -20px;
            right: -20px;
            background-image: url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 140 140"><g fill="%23e0672b" opacity="0.95"><circle cx="100" cy="30" r="15" fill="%23f47e3a"/><circle cx="80" cy="22" r="13" fill="%23ea6f31"/><circle cx="112" cy="45" r="12" fill="%23e5632a"/><circle cx="72" cy="45" r="10" fill="%23f58b48"/><circle cx="95" cy="55" r="14" fill="%23f6974a"/><circle cx="118" cy="22" r="9" fill="%23f7b179"/><circle cx="62" cy="30" r="8" fill="%23e68144"/><path d="M92 15 Q104 8 112 18" stroke="%236b4a2b" stroke-width="3" fill="none" stroke-opacity="0.7"/><path d="M112 60 Q100 50 86 54" stroke="%236b4a2b" stroke-width="3" fill="none" stroke-opacity="0.7"/><circle cx="78" cy="12" r="6" fill="%239bc35b" opacity="0.8"/></g></svg>');
            animation: bloomNaturalTR 5.5s infinite ease-in-out;
        }
        .corner-bl {
            bottom: -20px;
            left: -20px;
            background-image: url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 140 140"><g fill="%23e8a35c" opacity="0.95"><circle cx="32" cy="98" r="14" fill="%23f5b079"/><circle cx="48" cy="110" r="12" fill="%23e69758"/><circle cx="20" cy="84" r="11" fill="%23ee9e64"/><circle cx="55" cy="88" r="13" fill="%23e28f52"/><circle cx="35" cy="68" r="9" fill="%23f6c28d"/><circle cx="15" cy="110" r="8" fill="%23f3bc84"/><circle cx="62" cy="102" r="10" fill="%23dc894b"/><path d="M30 120 Q42 128 50 118" stroke="%236b4a2b" stroke-width="3" fill="none" stroke-opacity="0.7"/><path d="M22 78 Q32 72 45 78" stroke="%236b4a2b" stroke-width="3" fill="none" stroke-opacity="0.7"/><circle cx="45" cy="124" r="5" fill="%239bc35b" opacity="0.9"/></g></svg>');
            animation: bloomNaturalBL 6s infinite ease-in-out;
        }
        .corner-br {
            bottom: -20px;
            right: -20px;
            background-image: url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 140 140"><g fill="%23dd723b" opacity="0.95"><circle cx="100" cy="100" r="16" fill="%23ec7d3d"/><circle cx="80" cy="110" r="13" fill="%23f5914c"/><circle cx="115" cy="82" r="12" fill="%23e27d42"/><circle cx="70" cy="85" r="11" fill="%23f3a25d"/><circle cx="92" cy="70" r="9" fill="%23eaa364"/><circle cx="120" cy="112" r="10" fill="%23eb8749"/><circle cx="62" cy="100" r="8" fill="%23f5bb85"/><path d="M95 124 Q85 132 75 126" stroke="%236b4a2b" stroke-width="3" fill="none" stroke-opacity="0.7"/><path d="M112 72 Q100 66 88 73" stroke="%236b4a2b" stroke-width="3" fill="none" stroke-opacity="0.7"/><circle cx="108" cy="60" r="6" fill="%239bc35b" opacity="0.8"/></g></svg>');
            animation: bloomNaturalBR 5.2s infinite ease-in-out;
        }

        @keyframes bloomNaturalTL {
            0% { transform: scale(0.9) rotate(-6deg); opacity: 0.75; filter: drop-shadow(0 5px 6px #a34f22); }
            50% { transform: scale(1.18) rotate(-2deg); opacity: 1; filter: drop-shadow(0 16px 18px #b3531b); }
            100% { transform: scale(0.9) rotate(-6deg); opacity: 0.75; filter: drop-shadow(0 5px 6px #a34f22); }
        }
        @keyframes bloomNaturalTR {
            0% { transform: scale(0.92) rotate(5deg); opacity: 0.8; filter: drop-shadow(0 5px 8px #a9511e); }
            50% { transform: scale(1.2) rotate(2deg); opacity: 1; filter: drop-shadow(0 18px 18px #be571c); }
            100% { transform: scale(0.92) rotate(5deg); opacity: 0.8; filter: drop-shadow(0 5px 8px #a9511e); }
        }
        @keyframes bloomNaturalBL {
            0% { transform: scale(0.88) rotate(-8deg); opacity: 0.7; filter: drop-shadow(0 6px 8px #9d471d); }
            50% { transform: scale(1.15) rotate(-3deg); opacity: 1; filter: drop-shadow(0 18px 18px #ac4d1b); }
            100% { transform: scale(0.88) rotate(-8deg); opacity: 0.7; filter: drop-shadow(0 6px 8px #9d471d); }
        }
        @keyframes bloomNaturalBR {
            0% { transform: scale(0.9) rotate(9deg); opacity: 0.75; filter: drop-shadow(0 6px 8px #a84e1d); }
            50% { transform: scale(1.22) rotate(4deg); opacity: 1; filter: drop-shadow(0 20px 20px #c45a1c); }
            100% { transform: scale(0.9) rotate(9deg); opacity: 0.75; filter: drop-shadow(0 6px 8px #a84e1d); }
        }

        /* inner card styles (unchanged) */
        .card-header {
            height: 28px;
            width: 100%;
            background: linear-gradient(90deg, #c99e7b, #b5835a, #c99e7b);
            display: flex;
            justify-content: center;
            gap: 8px;
            box-shadow: inset 0 -2px 5px rgba(0,0,0,0.1);
            position: relative;
            z-index: 10;
        }

        .header-dot {
            width: 14px;
            height: 14px;
            background: #fdebd0;
            border-radius: 50%;
            margin: 7px 3px;
            box-shadow: 0 0 6px #ffe3b6;
            animation: pulseDots 2.4s infinite;
        }
        .header-dot:nth-child(2) { animation-delay: 0.4s; }
        .header-dot:nth-child(3) { animation-delay: 0.8s; }
        .header-dot:nth-child(4) { animation-delay: 1.2s; }
        .header-dot:nth-child(5) { animation-delay: 1.6s; }

        @keyframes pulseDots {
            0% { opacity: 0.6; transform: scale(0.9); background: #fbe6ce; }
            50% { opacity: 1; transform: scale(1.2); background: #ffefd1; box-shadow: 0 0 10px #fbd9a3; }
            100% { opacity: 0.6; transform: scale(0.9); background: #fbe6ce; }
        }

        .content {
            padding: 28px 20px 24px;
            text-align: center;
            position: relative;
            z-index: 20;
            font-family: 'Cormorant Garamond', serif;
        }

        .divider-flourish {
            font-size: 24px;
            letter-spacing: 10px;
            color: #b5835a;
            opacity: 0.7;
            margin: 8px 0 10px;
            animation: shine 3s infinite;
        }
        @keyframes shine {
            0% { opacity: 0.5; text-shadow: 0 0 0 #eaceb0; }
            50% { opacity: 1; text-shadow: 0 0 6px #e9b68a; }
            100% { opacity: 0.5; text-shadow: 0 0 0 #eaceb0; }
        }

        .names {
            font-family: 'Cormorant Garamond', serif;
            font-size: clamp(36px, 10vw, 46px);
            font-weight: 700;
            color: #3b281f;
            line-height: 1.2;
            text-transform: uppercase;
            letter-spacing: 3px;
            text-shadow: 2px 2px 0 #f3dbc4, 4px 4px 0 rgba(100, 60, 30, 0.2);
            margin-bottom: 8px;
            animation: floatNames 3s ease-in-out infinite;
        }
        @keyframes floatNames {
            0% { transform: translateY(0); }
            50% { transform: translateY(-3px); }
            100% { transform: translateY(0); }
        }
        .ampersand {
            font-size: 40px;
            font-weight: 500;
            font-style: italic;
            color: #b5835a;
            text-shadow: 0 0 8px #ebcbaa;
            margin: 0 4px;
        }

        .subtitle {
            font-size: clamp(18px, 4.5vw, 21px);
            letter-spacing: 3px;
            color: #7f5b48;
            text-transform: uppercase;
            font-weight: 500;
            border-top: 2px dashed #dbb994;
            border-bottom: 2px dashed #dbb994;
            padding: 12px 0;
            margin: 12px 0 16px;
            background: rgba(255, 240, 220, 0.4);
            animation: fadeSlide 2.2s infinite alternate;
        }
        @keyframes fadeSlide {
            0% { letter-spacing: 2px; opacity: 0.8; }
            100% { letter-spacing: 4px; opacity: 1; }
        }

        .engagement-tag {
            font-size: clamp(28px, 7vw, 34px);
            font-weight: 700;
            color: #4f3a2b;
            line-height: 1.3;
            margin: 8px 0;
            background: linear-gradient(90deg, #cc9f76, #aa7852, #cc9f76);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
            animation: sparkle 2s infinite;
        }
        @keyframes sparkle {
            0% { filter: drop-shadow(0 0 2px #e4b282); }
            50% { filter: drop-shadow(0 0 8px #e9c394); }
            100% { filter: drop-shadow(0 0 2px #e4b282); }
        }

        .date-block {
            background: #e7d6c0;
            border-radius: 80px;
            padding: 16px 10px;
            margin: 20px 0 18px;
            box-shadow: inset 0 2px 5px #dbbc95, 0 10px 12px -8px #755e4b;
            border: 1px solid #cbaa83;
            animation: gentlePulse 3s infinite;
        }
        @keyframes gentlePulse {
            0% { box-shadow: inset 0 2px 5px #dbbc95, 0 10px 12px -8px #755e4b; }
            50% { box-shadow: inset 0 2px 8px #eedbbb, 0 14px 16px -8px #946b50; }
            100% { box-shadow: inset 0 2px 5px #dbbc95, 0 10px 12px -8px #755e4b; }
        }
        .day-name { font-size: 24px; font-weight: 600; color: #3d2a1d; }
        .full-date { font-size: clamp(38px, 10vw, 48px); font-weight: 700; color: #512e1c; text-shadow: 2px 2px 0 #f1cfb5; }
        .time-info {
            font-size: clamp(22px, 5.5vw, 26px);
            font-weight: 500;
            background: #4e362b;
            color: #fce8d2;
            padding: 6px 18px;
            border-radius: 50px;
            display: inline-block;
            margin-top: 8px;
            box-shadow: 0 3px 0 #2f1f18;
            animation: bounceTime 2.8s infinite;
        }
        @keyframes bounceTime {
            0% { transform: scale(1); } 50% { transform: scale(1.02); background-color: #5f4134; } 100% { transform: scale(1); }
        }

        .venue {
            background: #fff8ed;
            border-radius: 40px;
            padding: 18px 12px;
            margin: 16px 0 18px;
            border: 2px dotted #ba8b63;
            color: #382b22;
            box-shadow: 0 4px 0 #9f7b60;
            transition: all 0.2s ease;
            cursor: pointer;
            text-decoration: none;
            display: block;
        }
        .venue:hover {
            background: #f5e7d6;
            border-color: #a57149;
            transform: scale(1.01) translateY(-2px);
            box-shadow: 0 8px 0 #9f7b60, 0 12px 20px rgba(100,50,20,0.25);
        }
        .venue:active { transform: scale(0.98); box-shadow: 0 2px 0 #9f7b60; }
        .venue p { margin: 6px 0; line-height: 1.45; font-size: clamp(16px, 4vw, 18px); font-weight: 500; }
        .venue-name {
            font-size: clamp(24px, 6.5vw, 28px);
            font-weight: 700;
            color: #6b3f2b;
            text-transform: uppercase;
            animation: colorShift 4s infinite;
        }
        @keyframes colorShift {
            0% { color: #6b3f2b; } 33% { color: #8f5b41; } 66% { color: #a97454; } 100% { color: #6b3f2b; }
        }
        .address-detail { font-size: 16px; border-top: 1px solid #e5c9af; padding-top: 10px; margin-top: 8px; }
        .map-hint { font-size: 15px; color: #b45f2e; margin-top: 6px; display: flex; align-items: center; justify-content: center; gap: 5px; animation: hintPulse 2s infinite; }
        @keyframes hintPulse { 0% { opacity: 0.7; } 50% { opacity: 1; } 100% { opacity: 0.7; } }

        .lunch {
            font-size: clamp(28px, 7.5vw, 34px);
            font-weight: 700;
            color: #4b2b1c;
            background: #eccdad;
            display: inline-block;
            padding: 6px 24px;
            border-radius: 60px;
            letter-spacing: 4px;
            border: 2px solid #b1805b;
            transform: rotate(-0.5deg);
            box-shadow: 0 6px 0 #9f7b62;
            animation: wiggle 2.2s infinite;
        }
        @keyframes wiggle {
            0% { transform: rotate(-0.5deg) scale(1); } 25% { transform: rotate(0.5deg) scale(1.02); } 50% { transform: rotate(-1deg) scale(1); } 75% { transform: rotate(0.8deg) scale(1.01); } 100% { transform: rotate(-0.5deg) scale(1); }
        }

        .footer-note {
            font-size: clamp(20px, 5.5vw, 22px);
            font-weight: 500;
            color: #7b5e4b;
            margin-top: 22px;
            border-top: 2px solid #d6b696;
            padding-top: 14px;
            font-style: italic;
            animation: appearSoft 3s infinite;
        }
        @keyframes appearSoft { 0% { opacity: 0.6; } 50% { opacity: 1; } 100% { opacity: 0.6; } }

        .ring-icon { font-size: 36px; filter: drop-shadow(0 4px 4px #bb8877); margin: 8px 0 -8px; animation: rotateRing 4s infinite linear; }
        @keyframes rotateRing { 0% { transform: rotateY(0deg); } 50% { transform: rotateY(20deg); } 100% { transform: rotateY(0deg); } }

        .tiny-stars { margin-top: 10px; font-size: 16px; color: #a7856a; letter-spacing: 3px; animation: twinkle 2.2s infinite; }
        @keyframes twinkle { 0% { opacity: 0.5; } 50% { opacity: 1; text-shadow: 0 0 4px gold; } 100% { opacity: 0.5; } }

        .content::before {
            content: '';
            position: absolute;
            top: 0; left: 0; width: 100%; height: 100%;
            pointer-events: none;
            background: url('data:image/svg+xml;utf8,<svg width="60" height="60" viewBox="0 0 60 60"><circle cx="10" cy="12" r="2.5" fill="%23dbb487" opacity="0.3"/><circle cx="48" cy="22" r="3" fill="%23c2a079" opacity="0.25"/><circle cx="32" cy="50" r="2" fill="%23a55533" opacity="0.2"/><circle cx="22" cy="8" r="2" fill="%23cf9f6e" opacity="0.25"/><circle cx="52" cy="42" r="2.5" fill="%23b3774b" opacity="0.3"/></svg>');
            background-repeat: repeat;
            opacity: 0.3;
            animation: confettiMove 22s infinite linear;
            z-index: 0;
        }
        @keyframes confettiMove { 0% { background-position: 0 0; } 100% { background-position: 80px 80px; } }
        .content > * { position: relative; z-index: 5; }
    </style>
</head>
<body>
    <div class="envelope-wrapper" id="envelopeWrapper">
        <div class="envelope closed" id="envelope">
            <div class="flap"></div>
            <!-- Engagement decorations on envelope (only visible when closed) -->
            <div class="envelope-decor">
                <div class="ring-decor ring-1"></div>
                <div class="ring-decor ring-2"></div>
                <div class="heart-decor heart-1">❤️</div>
                <div class="heart-decor heart-2">❤️</div>
                <div class="heart-decor heart-3">❤️</div>
                <div class="banner">✨ ENGAGEMENT ✨</div>
                <div class="confetti-dot dot1"></div>
                <div class="confetti-dot dot2"></div>
                <div class="confetti-dot dot3"></div>
            </div>
            <!-- invitation card with natural flower corners -->
            <div class="invitation-card">
                <div class="flower-corner corner-tl"></div>
                <div class="flower-corner corner-tr"></div>
                <div class="flower-corner corner-bl"></div>
                <div class="flower-corner corner-br"></div>
                <div class="card-header">
                    <div class="header-dot"></div><div class="header-dot"></div><div class="header-dot"></div><div class="header-dot"></div><div class="header-dot"></div>
                </div>
                <div class="content">
                    <div class="ring-icon">💍 🌸 💍</div>
                    <div class="divider-flourish">◈ ◈ ◈</div>
                    <div class="names"><span>PRUDHVI</span><br><span class="ampersand">&</span><br><span>MANASA</span></div>
                    <div class="divider-flourish">✽ ✽ ✽</div>
                    <div class="subtitle">are getting married!</div>
                    <div class="engagement-tag">PLEASE JOIN US IN CELEBRATION<br>OF THEIR ENGAGEMENT</div>
                    <div class="date-block">
                        <div class="day-name">SATURDAY</div>
                        <div class="full-date">14th MARCH 2026</div>
                        <div class="time-info">10:00 A.M. ONWARDS</div>
                    </div>
                    <a href="https://maps.google.com/?q=Kingston+Park+Nallagandla+Bypass+Road+Hyderabad+Beside+HP+Petrol+Pump" target="_blank" rel="noopener" class="venue">
                        <div class="venue-name">Kingston Park</div>
                        <p><strong>Nallagandla Bypass Road,</strong><br>Beside HP Petrol Pump,<br>Serilingampally, Hyderabad.</p>
                        <div class="address-detail">📍 landmark: beside HP petrol pump</div>
                        <div class="map-hint"><span>🗺️</span> tap to open maps <span>🗺️</span></div>
                    </a>
                    <div class="lunch">🍽️ LUNCH FOLLOWS 🍽️</div>
                    <div class="footer-note">— We await your blessings —</div>
                    <div class="tiny-stars">✦ ✦ ✦</div>
                </div>
            </div>
        </div>
        <div class="tap-hint">⟡  tap to open  ⟡</div>
    </div>

    <script>
        const envelope = document.getElementById('envelope');
        const wrapper = document.getElementById('envelopeWrapper');

        wrapper.addEventListener('click', function(e) {
            if (envelope.classList.contains('closed')) {
                envelope.classList.remove('closed');
                envelope.classList.add('open');
            }
        });
    </script>
</body>
</html>
