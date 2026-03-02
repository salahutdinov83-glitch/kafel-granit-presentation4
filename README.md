<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>КафельГранит × Bellezza Tech — Партнёрское предложение</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        :root {
            --gold: #D4AF37;
            --gold-light: #F4E8C1;
            --black: #0a0a0a;
            --dark-gray: #1a1a1a;
            --white: #ffffff;
            --bronze: #8B7355;
            --gray-text: #888888;
            --green: #00c853;
        }

        @import url('https://fonts.googleapis.com/css2?family=Playfair+Display:wght@400;700;900&family=Inter:wght@300;400;500;600;700&display=swap');

        html, body {
            font-family: 'Inter', sans-serif;
            background: var(--black);
            color: var(--white);
            height: 100%;
            width: 100%;
            overflow: hidden;
            font-size: 16px;
        }

        .presentation {
            width: 100%;
            height: 100%;
            position: relative;
        }

        .slide {
            position: absolute;
            width: 100%;
            height: 100%;
            display: none;
            opacity: 0;
            transition: opacity 0.6s ease-in-out;
            padding: 40px;
            background: linear-gradient(135deg, var(--black) 0%, var(--dark-gray) 100%);
            overflow: hidden;
        }

        .slide.active {
            display: flex;
            opacity: 1;
        }

        /* Навигация */
        .nav {
            position: fixed;
            bottom: 20px;
            left: 50%;
            transform: translateX(-50%);
            display: flex;
            gap: 8px;
            z-index: 1000;
            background: rgba(0,0,0,0.85);
            padding: 10px 18px;
            border-radius: 50px;
            backdrop-filter: blur(10px);
            border: 1px solid rgba(212,175,55,0.3);
        }

        .nav-btn {
            width: 10px;
            height: 10px;
            border-radius: 50%;
            background: rgba(255,255,255,0.3);
            border: none;
            cursor: pointer;
            transition: all 0.3s;
        }

        .nav-btn:hover, .nav-btn.active {
            background: var(--gold);
            transform: scale(1.3);
        }

        .nav-arrows {
            position: fixed;
            bottom: 20px;
            right: 20px;
            display: flex;
            gap: 8px;
            z-index: 1000;
        }

        .arrow-btn {
            width: 40px;
            height: 40px;
            border-radius: 50%;
            background: rgba(212,175,55,0.2);
            border: 1px solid var(--gold);
            color: var(--gold);
            font-size: 16px;
            cursor: pointer;
            transition: all 0.3s;
            display: flex;
            align-items: center;
            justify-content: center;
        }

        .arrow-btn:hover {
            background: var(--gold);
            color: var(--black);
            transform: scale(1.1);
        }

        /* Прогресс-бар */
        .progress-bar {
            position: fixed;
            top: 0;
            left: 0;
            height: 3px;
            background: linear-gradient(90deg, var(--gold), var(--bronze));
            transition: width 0.3s;
            z-index: 1001;
        }

        /* Номер слайда */
        .slide-number {
            position: fixed;
            top: 20px;
            right: 20px;
            font-size: 14px;
            color: rgba(255,255,255,0.5);
            z-index: 1000;
            background: rgba(0,0,0,0.5);
            padding: 5px 12px;
            border-radius: 15px;
        }

        .slide-number span {
            color: var(--gold);
            font-weight: 600;
        }

        /* ============================================
           СЛАЙД 1: ИНТРО
           ============================================ */
        .slide-1 {
            flex-direction: column;
            justify-content: center;
            align-items: center;
            text-align: center;
            background: 
                radial-gradient(circle at 30% 50%, rgba(212,175,55,0.1) 0%, transparent 50%),
                linear-gradient(135deg, var(--black) 0%, var(--dark-gray) 100%);
        }

        .logo-main {
            font-family: 'Playfair Display', serif;
            font-size: clamp(2.5rem, 5vw, 4rem);
            font-weight: 900;
            color: var(--gold);
            margin-bottom: 10px;
            letter-spacing: 5px;
            text-transform: uppercase;
        }

        .logo-sub {
            font-size: clamp(1rem, 2vw, 1.4rem);
            color: var(--gold-light);
            margin-bottom: 30px;
            letter-spacing: 10px;
        }

        .hook-text {
            font-size: clamp(1.5rem, 3vw, 2.4rem);
            max-width: 80%;
            line-height: 1.4;
            margin-bottom: 25px;
            font-weight: 300;
        }

        .hook-text span {
            color: var(--gold);
            font-weight: 600;
        }

        .patent-badge {
            display: inline-flex;
            align-items: center;
            gap: 10px;
            background: rgba(212,175,55,0.1);
            border: 1px solid var(--gold);
            padding: 12px 25px;
            border-radius: 50px;
            font-size: 14px;
            color: var(--gold);
            font-weight: 600;
        }

        .patent-badge::before {
            content: "★";
            font-size: 16px;
        }

        /* ============================================
           СЛАЙД 2: О КОМПАНИИ
           ============================================ */
        .slide-2 {
            flex-direction: row;
            align-items: center;
            gap: 30px;
        }

        .company-info {
            flex: 1.2;
            min-width: 0;
        }

        .company-visual {
            flex: 0.8;
            height: 60%;
            min-height: 300px;
            background: linear-gradient(135deg, rgba(212,175,55,0.1), rgba(139,115,85,0.1));
            border-radius: 20px;
            border: 1px solid rgba(212,175,55,0.3);
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            position: relative;
            overflow: hidden;
        }

        .company-visual::before {
            content: "";
            position: absolute;
            width: 200%;
            height: 200%;
            background: repeating-linear-gradient(45deg, transparent, transparent 20px, rgba(212,175,55,0.05) 20px, rgba(212,175,55,0.05) 40px);
            animation: slide 20s linear infinite;
        }

        @keyframes slide {
            0% { transform: translate(-50%, -50%); }
            100% { transform: translate(0, 0); }
        }

        .company-visual-content {
            position: relative;
            z-index: 1;
            text-align: center;
        }

        .company-visual-content .kg-logo {
            font-size: 5rem;
            color: var(--gold);
            font-family: 'Playfair Display', serif;
            font-weight: 900;
        }

        .company-visual-content .kg-text {
            font-size: 1.1rem;
            color: var(--gold-light);
            margin-top: 15px;
        }

        h2 {
            font-family: 'Playfair Display', serif;
            font-size: clamp(1.8rem, 3vw, 2.8rem);
            color: var(--gold);
            margin-bottom: 20px;
        }

        .company-desc {
            font-size: clamp(14px, 1.5vw, 18px);
            line-height: 1.6;
            color: rgba(255,255,255,0.8);
            margin-bottom: 20px;
        }

        .stats-grid {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 15px;
        }

        .stat-item {
            background: rgba(255,255,255,0.05);
            padding: 15px;
            border-radius: 12px;
            border-left: 3px solid var(--gold);
        }

        .stat-number {
            font-size: clamp(1.5rem, 2vw, 2.2rem);
            font-weight: 700;
            color: var(--gold);
            display: block;
        }

        .stat-label {
            font-size: 12px;
            color: rgba(255,255,255,0.7);
            margin-top: 5px;
            line-height: 1.3;
        }

        /* ============================================
           СЛАЙД 3: ПРОБЛЕМА
           ============================================ */
        .slide-3 {
            flex-direction: column;
            justify-content: center;
        }

        .problem-grid {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 20px;
            margin-top: 30px;
        }

        .problem-card {
            background: rgba(255,255,255,0.03);
            border: 1px solid rgba(255,255,255,0.1);
            padding: 25px 15px;
            border-radius: 15px;
            text-align: center;
            transition: all 0.3s;
        }

        .problem-card:hover {
            border-color: rgba(255,0,0,0.5);
            transform: translateY(-5px);
        }

        .problem-icon {
            font-size: 2.5rem;
            margin-bottom: 15px;
            opacity: 0.6;
        }

        .problem-card h3 {
            color: rgba(255,255,255,0.7);
            font-size: 14px;
            font-weight: 400;
            line-height: 1.3;
        }

        .vs-divider {
            text-align: center;
            margin: 25px 0;
            font-size: 1.2rem;
            color: var(--gold);
            font-weight: 600;
            position: relative;
        }

        .vs-divider::before,
        .vs-divider::after {
            content: "";
            position: absolute;
            top: 50%;
            width: 150px;
            height: 1px;
            background: linear-gradient(90deg, transparent, var(--gold));
        }

        .vs-divider::before { right: calc(50% + 30px); }
        .vs-divider::after { left: calc(50% + 30px); transform: rotate(180deg); }

        .solution-text {
            text-align: center;
            font-size: 1.3rem;
            color: var(--gold);
            font-weight: 600;
        }

        /* ============================================
           ТЕХНОЛОГИЧЕСКИЕ СЛАЙДЫ
           ============================================ */
        .tech-slide {
            flex-direction: row;
            align-items: center;
            gap: 40px;
        }

        .tech-content {
            flex: 1;
            min-width: 0;
        }

        .tech-visual {
            flex: 0.9;
            height: 55%;
            min-height: 280px;
            border-radius: 20px;
            position: relative;
            overflow: hidden;
            display: flex;
            align-items: center;
            justify-content: center;
        }

        .tech-badge {
            display: inline-block;
            padding: 8px 18px;
            border-radius: 50px;
            font-weight: 600;
            font-size: 12px;
            margin-bottom: 15px;
            text-transform: uppercase;
            letter-spacing: 2px;
        }

        .tech-badge.gold { background: var(--gold); color: var(--black); }
        .tech-badge.green { background: var(--green); color: var(--black); }
        .tech-badge.blue { background: #0080ff; color: var(--white); }

        .tech-title {
            font-family: 'Playfair Display', serif;
            font-size: clamp(2rem, 3vw, 3.2rem);
            margin-bottom: 15px;
            line-height: 1.2;
        }

        .tech-title.gold { color: var(--gold); }
        .tech-title.green { color: var(--green); }
        .tech-title.blue { color: #0080ff; }

        .tech-desc {
            font-size: clamp(14px, 1.5vw, 18px);
            line-height: 1.5;
            color: rgba(255,255,255,0.8);
            margin-bottom: 20px;
        }

        .tech-feature {
            display: flex;
            align-items: center;
            gap: 10px;
            margin: 10px 0;
            font-size: 15px;
        }

        .tech-feature::before {
            content: "→";
            color: var(--gold);
            font-weight: bold;
        }

        .tech-visual-content {
            text-align: center;
            z-index: 1;
        }

        .tech-visual-icon {
            font-size: 5rem;
            margin-bottom: 15px;
        }

        .tech-visual-text {
            font-size: 1.3rem;
            font-weight: 600;
        }

        .glow-effect {
            position: absolute;
            width: 100%;
            height: 100%;
            background: radial-gradient(circle at center, rgba(212,175,55,0.3) 0%, transparent 70%);
            animation: pulse 3s ease-in-out infinite;
        }

        .glow-effect.green {
            background: radial-gradient(circle at center, rgba(0,255,100,0.2) 0%, transparent 70%);
        }

        .glow-effect.blue {
            background: radial-gradient(circle at center, rgba(0,128,255,0.2) 0%, transparent 70%);
        }

        @keyframes pulse {
            0%, 100% { opacity: 0.5; transform: scale(1); }
            50% { opacity: 0.8; transform: scale(1.1); }
        }

        /* ============================================
           СЛАЙД 7: CER-SINK FULL
           ============================================ */
        .slide-7 {
            flex-direction: row;
            align-items: center;
            gap: 40px;
        }

        .sink-showcase {
            flex: 1;
            height: 65%;
            min-height: 320px;
            position: relative;
            border-radius: 20px;
            overflow: hidden;
            background: linear-gradient(135deg, #2a2a2a, #1a1a1a);
            border: 2px solid rgba(212,175,55,0.3);
            display: flex;
            align-items: center;
            justify-content: center;
        }

        .sink-placeholder {
            text-align: center;
        }

        .sink-placeholder-icon {
            font-size: 6rem;
            margin-bottom: 15px;
        }

        .sink-placeholder-text {
            color: var(--gray-text);
            font-size: 14px;
        }

        .sink-overlay {
            position: absolute;
            bottom: 0;
            left: 0;
            right: 0;
            background: linear-gradient(to top, rgba(0,0,0,0.9), transparent);
            padding: 25px;
        }

        .sink-label {
            color: var(--gold);
            font-size: 12px;
            text-transform: uppercase;
            letter-spacing: 3px;
            margin-bottom: 5px;
        }

        .sink-name {
            font-family: 'Playfair Display', serif;
            font-size: 1.5rem;
            color: var(--white);
        }

        .sink-content {
            flex: 1;
            min-width: 0;
        }

        .sink-badge {
            display: inline-block;
            background: linear-gradient(135deg, #666, #888);
            color: var(--white);
            padding: 8px 18px;
            border-radius: 50px;
            font-weight: 600;
            font-size: 12px;
            margin-bottom: 15px;
            text-transform: uppercase;
            letter-spacing: 2px;
        }

        .sink-title {
            font-family: 'Playfair Display', serif;
            font-size: clamp(2rem, 3vw, 3.2rem);
            margin-bottom: 15px;
            line-height: 1.2;
            color: var(--white);
        }

        .sink-desc {
            font-size: clamp(14px, 1.5vw, 18px);
            line-height: 1.5;
            color: rgba(255,255,255,0.8);
            margin-bottom: 20px;
        }

        .sink-benefits {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 12px;
        }

        .sink-benefit {
            background: rgba(255,255,255,0.05);
            padding: 12px;
            border-radius: 10px;
            border-left: 3px solid var(--gold);
        }

        .sink-benefit h4 {
            color: var(--gold);
            margin-bottom: 5px;
            font-size: 14px;
        }

        .sink-benefit p {
            color: rgba(255,255,255,0.7);
            font-size: 12px;
            line-height: 1.3;
        }

        /* ============================================
           СЛАЙД 8: ТЕСТЫ
           ============================================ */
        .slide-8 {
            flex-direction: column;
            justify-content: center;
        }

        .slide-8 h2 {
            margin-bottom: 10px;
        }

        .slide-subtitle {
            font-size: 16px;
            color: rgba(255,255,255,0.7);
            margin-bottom: 25px;
        }

        .test-grid {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 15px;
            margin-top: 20px;
        }

        .test-card {
            background: rgba(255,255,255,0.05);
            border-radius: 15px;
            padding: 20px;
            text-align: center;
            border: 1px solid rgba(212,175,55,0.2);
            transition: all 0.3s;
        }

        .test-card:hover {
            border-color: var(--gold);
            transform: translateY(-3px);
        }

        .test-icon {
            font-size: 3rem;
            margin-bottom: 12px;
            display: block;
        }

        .test-name {
            font-size: 16px;
            font-weight: 600;
            color: var(--gold);
            margin-bottom: 8px;
        }

        .test-result {
            font-size: 13px;
            color: rgba(255,255,255,0.8);
        }

        /* ============================================
           СЛАЙД 9: ПРОДУКТЫ
           ============================================ */
        .slide-9 {
            flex-direction: column;
        }

        .products-grid {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 20px;
            margin-top: 25px;
            flex: 1;
        }

        .product-card {
            background: rgba(255,255,255,0.03);
            border-radius: 15px;
            padding: 25px;
            border: 1px solid rgba(255,255,255,0.1);
            transition: all 0.3s;
            display: flex;
            flex-direction: column;
        }

        .product-card:hover {
            border-color: var(--gold);
            background: rgba(212,175,55,0.05);
        }

        .product-icon {
            font-size: 2.5rem;
            margin-bottom: 15px;
        }

        .product-title {
            font-size: 1.3rem;
            font-weight: 600;
            margin-bottom: 12px;
            color: var(--gold-light);
        }

        .product-list {
            list-style: none;
            font-size: 14px;
            color: rgba(255,255,255,0.7);
            flex: 1;
        }

        .product-list li {
            margin: 6px 0;
            padding-left: 15px;
            position: relative;
        }

        .product-list li::before {
            content: "•";
            color: var(--gold);
            position: absolute;
            left: 0;
        }

        .product-highlight {
            background: rgba(212,175,55,0.1);
            border: 1px solid var(--gold);
            border-radius: 8px;
            padding: 10px;
            margin-top: 15px;
            font-size: 13px;
            color: var(--gold);
            font-weight: 600;
        }

        /* ============================================
           СЛАЙД 10: КЕЙСЫ
           ============================================ */
        .slide-10 {
            flex-direction: column;
        }

        .cases-header {
            text-align: center;
            margin-bottom: 20px;
        }

        .cases-subtitle {
            font-size: 16px;
            color: rgba(255,255,255,0.7);
            margin-top: 8px;
        }

        .cases-grid {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 15px;
            flex: 1;
        }

        .case-card {
            background: rgba(255,255,255,0.03);
            border-radius: 15px;
            padding: 18px;
            border: 1px solid rgba(255,255,255,0.1);
            transition: all 0.3s;
            position: relative;
            overflow: hidden;
            display: flex;
            flex-direction: column;
        }

        .case-card:hover {
            border-color: var(--gold);
            transform: translateY(-3px);
        }

        .case-card::before {
            content: "";
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 3px;
            background: linear-gradient(90deg, var(--gold), var(--bronze));
        }

        .case-number {
            position: absolute;
            top: 12px;
            right: 15px;
            font-size: 2.5rem;
            font-weight: 900;
            color: rgba(212,175,55,0.1);
            font-family: 'Playfair Display', serif;
        }

        .case-title {
            font-size: 15px;
            font-weight: 600;
            color: var(--gold);
            margin-bottom: 12px;
            padding-right: 40px;
        }

        .case-specs {
            margin-bottom: 12px;
            flex: 1;
        }

        .case-spec {
            display: flex;
            justify-content: space-between;
            padding: 6px 0;
            border-bottom: 1px solid rgba(255,255,255,0.1);
            font-size: 13px;
        }

        .case-spec:last-child {
            border-bottom: none;
        }

        .case-spec-label {
            color: rgba(255,255,255,0.6);
        }

        .case-spec-value {
            color: var(--white);
            font-weight: 500;
        }

        .case-profit {
            background: rgba(0,200,83,0.1);
            border: 1px solid var(--green);
            border-radius: 10px;
            padding: 12px;
            text-align: center;
            margin-top: auto;
        }

        .case-profit-label {
            font-size: 11px;
            color: rgba(255,255,255,0.7);
            text-transform: uppercase;
            letter-spacing: 1px;
            margin-bottom: 5px;
        }

        .case-profit-value {
            font-size: 1.8rem;
            font-weight: 700;
            color: var(--green);
        }

        .case-margin {
            font-size: 13px;
            color: rgba(255,255,255,0.8);
            margin-top: 3px;
        }

        /* ============================================
           СЛАЙД 11: ПАРТНЁРСТВО
           ============================================ */
        .slide-11 {
            flex-direction: row;
            align-items: center;
            gap: 40px;
        }

        .partnership-content {
            flex: 1.3;
            min-width: 0;
        }

        .partnership-intro {
            font-size: 16px;
            color: rgba(255,255,255,0.8);
            margin-bottom: 20px;
        }

        .benefits-list {
            display: flex;
            flex-direction: column;
            gap: 12px;
        }

        .benefit-item {
            display: flex;
            align-items: flex-start;
            gap: 15px;
            padding: 15px;
            background: rgba(255,255,255,0.03);
            border-radius: 12px;
            border-left: 3px solid var(--gold);
            transition: all 0.3s;
        }

        .benefit-item:hover {
            background: rgba(212,175,55,0.05);
            transform: translateX(5px);
        }

        .benefit-number {
            font-size: 1.5rem;
            font-weight: 700;
            color: var(--gold);
            line-height: 1;
            min-width: 30px;
        }

        .benefit-text h4 {
            font-size: 16px;
            margin-bottom: 3px;
            color: var(--white);
        }

        .benefit-text p {
            font-size: 13px;
            color: rgba(255,255,255,0.7);
            line-height: 1.4;
        }

        .partnership-visual {
            flex: 0.7;
            height: 60%;
            min-height: 300px;
            background: linear-gradient(135deg, rgba(212,175,55,0.1), rgba(139,115,85,0.1));
            border: 2px solid var(--gold);
            border-radius: 20px;
            display: flex;
            align-items: center;
            justify-content: center;
        }

        .partnership-visual-content {
            text-align: center;
            padding: 20px;
        }

        .margin-icon {
            font-size: 3rem;
            margin-bottom: 15px;
        }

        .margin-value {
            font-size: 2.5rem;
            color: var(--gold);
            font-weight: 700;
            margin-bottom: 8px;
        }

        .margin-label {
            font-size: 14px;
            color: rgba(255,255,255,0.8);
            line-height: 1.4;
        }

        /* ============================================
           СЛАЙД 12: КОНТАКТЫ
           ============================================ */
        .slide-12 {
            flex-direction: column;
            justify-content: center;
            align-items: center;
            text-align: center;
            background: 
                radial-gradient(circle at 70% 50%, rgba(212,175,55,0.15) 0%, transparent 50%),
                linear-gradient(135deg, var(--black) 0%, var(--dark-gray) 100%);
        }

        .final-title {
            font-family: 'Playfair Display', serif;
            font-size: clamp(2rem, 3.5vw, 3.2rem);
            margin-bottom: 15px;
            color: var(--gold);
        }

        .final-subtitle {
            font-size: clamp(16px, 2vw, 20px);
            color: rgba(255,255,255,0.8);
            margin-bottom: 35px;
            max-width: 70%;
        }

        .contacts-grid {
            display: flex;
            gap: 20px;
            margin-bottom: 30px;
            flex-wrap: wrap;
            justify-content: center;
        }

        .contact-item {
            background: rgba(255,255,255,0.05);
            padding: 18px 30px;
            border-radius: 15px;
            border: 1px solid rgba(212,175,55,0.3);
            transition: all 0.3s;
        }

        .contact-item:hover {
            background: rgba(212,175,55,0.1);
            transform: scale(1.05);
        }

        .contact-label {
            font-size: 12px;
            color: var(--gold);
            text-transform: uppercase;
            letter-spacing: 2px;
            margin-bottom: 6px;
        }

        .contact-value {
            font-size: 1.3rem;
            font-weight: 600;
            color: var(--white);
        }

        .contact-value.small {
            font-size: 1.1rem;
        }

        .cta-button {
            display: inline-block;
            background: linear-gradient(135deg, var(--gold), var(--bronze));
            color: var(--black);
            padding: 15px 45px;
            border-radius: 50px;
            font-size: 18px;
            font-weight: 700;
            text-decoration: none;
            margin-top: 15px;
            transition: all 0.3s;
            box-shadow: 0 10px 30px rgba(212,175,55,0.3);
            cursor: pointer;
            border: none;
        }

        .cta-button:hover {
            transform: translateY(-3px);
            box-shadow: 0 15px 40px rgba(212,175,55,0.4);
        }

        .logos-footer {
            display: flex;
            gap: 25px;
            margin-top: 40px;
            align-items: center;
        }

        .footer-logo {
            font-family: 'Playfair Display', serif;
            font-size: 1.3rem;
            color: rgba(255,255,255,0.5);
        }

        .footer-logo.gold {
            color: var(--gold);
        }

        /* ============================================
           АДАПТИВНОСТЬ
           ============================================ */
        @media (max-width: 1200px) {
            .slide {
                padding: 30px;
            }

            .problem-grid {
                grid-template-columns: repeat(2, 1fr);
            }

            .test-grid {
                grid-template-columns: repeat(2, 1fr);
            }
        }

        @media (max-width: 1024px) {
            .slide-2, .slide-7, .slide-11 {
                flex-direction: column;
                gap: 20px;
            }

            .company-visual, .sink-showcase, .partnership-visual {
                height: 40%;
                width: 100%;
            }

            .tech-slide {
                flex-direction: column;
                gap: 20px;
            }

            .tech-visual {
                height: 40%;
                width: 100%;
                order: -1;
            }

            .products-grid {
                grid-template-columns: 1fr;
            }

            .cases-grid {
                grid-template-columns: 1fr;
            }

            .contacts-grid {
                flex-direction: column;
                gap: 12px;
            }

            .sink-benefits {
                grid-template-columns: 1fr;
            }
        }

        @media (max-width: 768px) {
            .problem-grid, .test-grid {
                grid-template-columns: 1fr;
            }

            .stats-grid {
                grid-template-columns: 1fr;
            }

            .hook-text {
                font-size: 1.3rem;
            }

            .logo-main {
                font-size: 2rem;
            }
        }
    </style>
</head>
<body>
    <div class="progress-bar" id="progressBar"></div>
    <div class="slide-number"><span id="currentSlideNum">1</span> / 12</div>

    <div class="presentation">
        <!-- Слайд 1: Интро -->
        <div class="slide slide-1 active" data-slide="1">
            <div class="logo-main">Bellezza Tech</div>
            <div class="logo-sub">КАФЕЛЬГРАНИТ</div>
            <h1 class="hook-text">
                Что, если столешница может <span>готовить еду сама</span>?<br>
                Без плиты. Без комфорок. Без чёрных квадратов.
            </h1>
            <div class="patent-badge">Международный патент</div>
        </div>

        <!-- Слайд 2: О компании -->
        <div class="slide slide-2" data-slide="2">
            <div class="company-info">
                <h2>КафельГранит</h2>
                <p class="company-desc">
                    Пять лет создаём мебель из керамики и спеченного камня. 
                    Каждый третий пост в Pinterest — о камне в интерьере. 
                    Итальянцы на АртДом уже не привозят кухни без каменных столешниц.
                </p>
                <div class="stats-grid">
                    <div class="stat-item">
                        <span class="stat-number">600 м²</span>
                        <span class="stat-label">Собственное производство<br>г. Красноярск</span>
                    </div>
                    <div class="stat-item">
                        <span class="stat-number">5+ лет</span>
                        <span class="stat-label">Опыт работы<br>с инновационными материалами</span>
                    </div>
                    <div class="stat-item">
                        <span class="stat-number">12</span>
                        <span class="stat-label">Реализованных проектов<br>с индукцией (3 в Москву)</span>
                    </div>
                    <div class="stat-item">
                        <span class="stat-number">2-3 недели</span>
                        <span class="stat-label">Срок изготовления<br>от замеров до монтажа</span>
                    </div>
                </div>
            </div>
            <div class="company-visual">
                <div class="company-visual-content">
                    <div class="kg-logo">КГ</div>
                    <div class="kg-text">Каменная эстетика</div>
                </div>
            </div>
        </div>

        <!-- Слайд 3: Проблема -->
        <div class="slide slide-3" data-slide="3">
            <h2>Проблема традиционных решений</h2>
            <div class="problem-grid">
                <div class="problem-card">
                    <div class="problem-icon">🔪</div>
                    <h3>Царапаются от ножа</h3>
                </div>
                <div class="problem-card">
                    <div class="problem-icon">🔥</div>
                    <h3>Боятся высоких температур</h3>
                </div>
                <div class="problem-card">
                    <div class="problem-icon">🍷</div>
                    <h3>Впитывают пятна</h3>
                </div>
                <div class="problem-card">
                    <div class="problem-icon">⬛</div>
                    <h3>Варочные панели портят интерьер</h3>
                </div>
            </div>
            <div class="vs-divider">НОВЫЙ СТАНДАРТ</div>
            <p class="solution-text">Технологии, которые меняют правила игры</p>
        </div>

        <!-- Слайд 4: Invisible -->
        <div class="slide tech-slide slide-4" data-slide="4">
            <div class="tech-content">
                <div class="tech-badge gold">Bellezza Tech</div>
                <h2 class="tech-title gold">INVISIBLE</h2>
                <p class="tech-desc">
                    Скрытая индукция под столешницей. Нет видимых комфорок — 
                    только чистый мрамор. Готовьте прямо на камне.
                </p>
                <div class="tech-feature">Индукционные элементы под поверхностью</div>
                <div class="tech-feature">Абсолютно ровная текстура камня</div>
                <div class="tech-feature">Международный патент на технологию</div>
            </div>
            <div class="tech-visual" style="background: linear-gradient(135deg, #1a1a1a, #2a2a2a);">
                <div class="glow-effect"></div>
                <div class="tech-visual-content">
                    <div class="tech-visual-icon">🔥</div>
                    <div class="tech-visual-text" style="color: var(--gold);">Индукция под камнем</div>
                </div>
            </div>
        </div>

        <!-- Слайд 5: Energy -->
        <div class="slide tech-slide slide-5" data-slide="5">
            <div class="tech-visual" style="background: linear-gradient(135deg, #0a1a0a, #1a2a1a);">
                <div class="glow-effect green"></div>
                <div class="tech-visual-content">
                    <div class="tech-visual-icon">⚡</div>
                    <div class="tech-visual-text" style="color: var(--green);">Беспроводная зарядка</div>
                </div>
            </div>
            <div class="tech-content">
                <div class="tech-badge green">Bellezza Tech</div>
                <h2 class="tech-title green">ENERGY</h2>
                <p class="tech-desc">
                    Беспроводная зарядка встроена в столешницу. 
                    Просто положите телефон — он начнёт заряжаться.
                </p>
                <div class="tech-feature">Работает на острове и рабочей зоне</div>
                <div class="tech-feature">Совместимость со всеми Qi-устройствами</div>
                <div class="tech-feature">Не заметна визуально</div>
            </div>
        </div>

        <!-- Слайд 6: Smart -->
        <div class="slide tech-slide slide-6" data-slide="6">
            <div class="tech-content">
                <div class="tech-badge blue">Bellezza Tech</div>
                <h2 class="tech-title blue">SMART</h2>
                <p class="tech-desc">
                    Интеграция с системами «Умный дом». 
                    Управление со смартфона. Будущее, доступное сегодня.
                </p>
                <div class="tech-feature">Управление индукцией через приложение</div>
                <div class="tech-feature">Интеграция с Alexa, Google Home, Apple HomeKit</div>
                <div class="tech-feature">Программирование сценариев работы</div>
            </div>
            <div class="tech-visual" style="background: linear-gradient(135deg, #0a0a1a, #1a1a2a);">
                <div class="glow-effect blue"></div>
                <div class="tech-visual-content">
                    <div class="tech-visual-icon">🏠</div>
                    <div class="tech-visual-text" style="color: #0080ff;">Умный дом в камне</div>
                </div>
            </div>
        </div>

        <!-- Слайд 7: CER-SINK FULL -->
        <div class="slide slide-7" data-slide="7">
            <div class="sink-showcase">
                <div class="sink-placeholder">
                    <div class="sink-placeholder-icon">🚰</div>
                    <div class="sink-placeholder-text">[Ваше фото мойки Cer-Sink Full]</div>
                </div>
                <div class="sink-overlay">
                    <div class="sink-label">Интегрированная система</div>
                    <div class="sink-name">Cer-Sink Full</div>
                </div>
            </div>
            <div class="sink-content">
                <div class="sink-badge">Новинка</div>
                <h2 class="sink-title">Мойка = Столешница</h2>
                <p class="sink-desc">
                    Уникальная система интегрированных кухонных моек. 
                    Никаких швов, никаких герметиков, никакой плесени. 
                    Мойка и столешница изготовлены из единого куска камня.
                </p>
                <div class="sink-benefits">
                    <div class="sink-benefit">
                        <h4>Идеальная гигиена</h4>
                        <p>Нет щелей для бактерий и грязи</p>
                    </div>
                    <div class="sink-benefit">
                        <h4>Единый декор</h4>
                        <p>Мойка и столешница в одном цвете</p>
                    </div>
                    <div class="sink-benefit">
                        <h4>Вечный срок службы</h4>
                        <p>Не протекает, не отклеивается</p>
                    </div>
                    <div class="sink-benefit">
                        <h4>Визуальная чистота</h4>
                        <p>Бесшовное решение премиум-класса</p>
                    </div>
                </div>
            </div>
        </div>

        <!-- Слайд 8: Тесты -->
        <div class="slide slide-8" data-slide="8">
            <h2>Материал, который неубиваем</h2>
            <p class="slide-subtitle">Режьте, лейте, жарьте, рубите — идеальная поверхность останется идеальной</p>
            <div class="test-grid">
                <div class="test-card">
                    <span class="test-icon">🔪</span>
                    <div class="test-name">Режем ножом</div>
                    <div class="test-result">Нет царапин</div>
                </div>
                <div class="test-card">
                    <span class="test-icon">🍷</span>
                    <div class="test-name">Льём вино/сок</div>
                    <div class="test-result">Не впитывается</div>
                </div>
                <div class="test-card">
                    <span class="test-icon">🔥</span>
                    <div class="test-name">Жарим горелкой</div>
                    <div class="test-result">Нет следов ожога</div>
                </div>
                <div class="test-card">
                    <span class="test-icon">🪓</span>
                    <div class="test-name">Рубим топором</div>
                    <div class="test-result">Поверхность цела</div>
                </div>
            </div>
        </div>

        <!-- Слайд 9: Продукты -->
        <div class="slide slide-9" data-slide="9">
            <h2>Продуктовая линейка</h2>
            <div class="products-grid">
                <div class="product-card">
                    <div class="product-icon">🍳</div>
                    <div class="product-title">Кухни</div>
                    <ul class="product-list">
                        <li>Столешницы с индукцией</li>
                        <li>Кухонные острова</li>
                        <li>Фартуки</li>
                        <li>Обеденные столы</li>
                    </ul>
                    <div class="product-highlight">
                        ⭐ Cer-Sink Full — интегрированные мойки
                    </div>
                </div>
                <div class="product-card">
                    <div class="product-icon">🛁</div>
                    <div class="product-title">Ванные комнаты</div>
                    <ul class="product-list">
                        <li>Раковины</li>
                        <li>Столешницы</li>
                        <li>Ванны</li>
                        <li>Аксессуары</li>
                    </ul>
                </div>
                <div class="product-card">
                    <div class="product-icon">🚪</div>
                    <div class="product-title">Фасады и элементы</div>
                    <ul class="product-list">
                        <li>Мебельные фасады</li>
                        <li>Лестничные ступени</li>
                        <li>Подоконники</li>
                        <li>Откосы</li>
                    </ul>
                </div>
            </div>
        </div>

        <!-- Слайд 10: Кейсы -->
        <div class="slide slide-10" data-slide="10">
            <div class="cases-header">
                <h2>Сколько зарабатывает партнёр</h2>
                <p class="cases-subtitle">Реальные цифры проектов с маржой от 100% до 250%</p>
            </div>
            <div class="cases-grid">
                <div class="case-card">
                    <div class="case-number">01</div>
                    <div class="case-title">Кухня 3 м с индукцией INVISIBLE</div>
                    <div class="case-specs">
                        <div class="case-spec">
                            <span class="case-spec-label">Состав</span>
                            <span class="case-spec-value">Столешница 3 м, 2 комфорки</span>
                        </div>
                        <div class="case-spec">
                            <span class="case-spec-label">Ваша цена партнёру</span>
                            <span class="case-spec-value">117 000 ₽</span>
                        </div>
                        <div class="case-spec">
                            <span class="case-spec-label">Рекомендуемая цена</span>
                            <span class="case-spec-value">280 000–320 000 ₽</span>
                        </div>
                    </div>
                    <div class="case-profit">
                        <div class="case-profit-label">Прибыль партнёра</div>
                        <div class="case-profit-value">163 000–203 000 ₽</div>
                        <div class="case-margin">Маржа: 140–175%</div>
                    </div>
                </div>

                <div class="case-card">
                    <div class="case-number">02</div>
                    <div class="case-title">Остров с комплексом технологий</div>
                    <div class="case-specs">
                        <div class="case-spec">
                            <span class="case-spec-label">Состав</span>
                            <span class="case-spec-value">Остров 2000×800 + индукция + зарядка</span>
                        </div>
                        <div class="case-spec">
                            <span class="case-spec-label">Ваша цена партнёру</span>
                            <span class="case-spec-value">145 000 ₽</span>
                        </div>
                        <div class="case-spec">
                            <span class="case-spec-label">Рекомендуемая цена</span>
                            <span class="case-spec-value">380 000–450 000 ₽</span>
                        </div>
                    </div>
                    <div class="case-profit">
                        <div class="case-profit-label">Прибыль партнёра</div>
                        <div class="case-profit-value">235 000–305 000 ₽</div>
                        <div class="case-margin">Маржа: 162–210%</div>
                    </div>
                </div>

                <div class="case-card">
                    <div class="case-number">03</div>
                    <div class="case-title">Комплекс «Премиум кухня»</div>
                    <div class="case-specs">
                        <div class="case-spec">
                            <span class="case-spec-label">Состав</span>
                            <span class="case-spec-value">Кухня 4 м + остров + мойка Cer-Sink</span>
                        </div>
                        <div class="case-spec">
                            <span class="case-spec-label">Ваша цена партнёру</span>
                            <span class="case-spec-value">244 000 ₽</span>
                        </div>
                        <div class="case-spec">
                            <span class="case-spec-label">Рекомендуемая цена</span>
                            <span class="case-spec-value">700 000–850 000 ₽</span>
                        </div>
                    </div>
                    <div class="case-profit">
                        <div class="case-profit-label">Прибыль партнёра</div>
                        <div class="case-profit-value">456 000–606 000 ₽</div>
                        <div class="case-margin">Маржа: 187–248%</div>
                    </div>
                </div>

                <div class="case-card">
                    <div class="case-number">04</div>
                    <div class="case-title">Мебельные фасады 12 м²</div>
                    <div class="case-specs">
                        <div class="case-spec">
                            <span class="case-spec-label">Состав</span>
                            <span class="case-spec-value">Фасады кухни из камня</span>
                        </div>
                        <div class="case-spec">
                            <span class="case-spec-label">Ваша цена партнёру</span>
                            <span class="case-spec-value">324 000 ₽ (27 000 ₽/м²)</span>
                        </div>
                        <div class="case-spec">
                            <span class="case-spec-label">Рекомендуемая цена</span>
                            <span class="case-spec-value">650 000–750 000 ₽</span>
                        </div>
                    </div>
                    <div class="case-profit">
                        <div class="case-profit-label">Прибыль партнёра</div>
                        <div class="case-profit-value">326 000–426 000 ₽</div>
                        <div class="case-margin">Маржа: 101–131%</div>
                    </div>
                </div>
            </div>
        </div>

        <!-- Слайд 11: Партнёрство -->
        <div class="slide slide-11" data-slide="11">
            <div class="partnership-content">
                <h2>Партнёрство с Bellezza Tech</h2>
                <p class="partnership-intro">
                    Премиум-сегмент с маржой в 3–5 раз выше рынка. Дизайнеры уже спрашивают.
                </p>
                <div class="benefits-list">
                    <div class="benefit-item">
                        <div class="benefit-number">01</div>
                        <div class="benefit-text">
                            <h4>Уникальный продукт</h4>
                            <p>Международный патент. Конкурентов нет. Технологии Invisible + Cer-Sink Full.</p>
                        </div>
                    </div>
                    <div class="benefit-item">
                        <div class="benefit-number">02</div>
                        <div class="benefit-text">
                            <h4>Полный цикл под ключ</h4>
                            <p>Замеры, изготовление, доставка, монтаж — берём всё на себя.</p>
                        </div>
                    </div>
                    <div class="benefit-item">
                        <div class="benefit-number">03</div>
                        <div class="benefit-text">
                            <h4>Гибкие условия</h4>
                            <p>Скидка 40% от розницы. Отсрочка 2 недели. Заказ от 1 изделия.</p>
                        </div>
                    </div>
                    <div class="benefit-item">
                        <div class="benefit-number">04</div>
                        <div class="benefit-text">
                            <h4>Гарантия и надёжность</h4>
                            <p>12 месяцев на изделие, 36 месяцев на индукцию. 12 реализованных проектов.</p>
                        </div>
                    </div>
                </div>
            </div>
            <div class="partnership-visual">
                <div class="partnership-visual-content">
                    <div class="margin-icon">📈</div>
                    <div class="margin-value">100–250%</div>
                    <div class="margin-label">маржа партнёра<br>vs 30–50% на рынке</div>
                </div>
            </div>
        </div>

        <!-- Слайд 12: Контакты -->
        <div class="slide slide-12" data-slide="12">
            <h1 class="final-title">Давайте обсудим вашу прибыль</h1>
            <p class="final-subtitle">
                Запишитесь на презентацию-знакомство с дегустацией технологий
            </p>

            <div class="contacts-grid">
                <div class="contact-item">
                    <div class="contact-label">Телефон</div>
                    <div class="contact-value">8 (902) 978-63-02</div>
                </div>
                <div class="contact-item">
                    <div class="contact-label">Телефон</div>
                    <div class="contact-value">8 (983) 700-49-29</div>
                </div>
                <div class="contact-item">
                    <div class="contact-label">Email</div>
                    <div class="contact-value small">89029786302@bk.ru</div>
                </div>
            </div>

            <button class="cta-button" onclick="alert('Позвоните нам: 8 (902) 978-63-02')">Позвонить сейчас</button>

            <div class="logos-footer">
                <div class="footer-logo gold">Bellezza Tech</div>
                <div style="color: rgba(255,255,255,0.3);">×</div>
                <div class="footer-logo">КАФЕЛЬГРАНИТ</div>
            </div>
        </div>
    </div>

    <!-- Навигация -->
    <div class="nav" id="navDots"></div>
    <div class="nav-arrows">
        <button class="arrow-btn" onclick="prevSlide()">←</button>
        <button class="arrow-btn" onclick="nextSlide()">→</button>
    </div>

    <script>
        let currentSlide = 1;
        const totalSlides = 12;

        function init() {
            const navContainer = document.getElementById('navDots');
            for (let i = 1; i <= totalSlides; i++) {
                const dot = document.createElement('button');
                dot.className = 'nav-btn' + (i === 1 ? ' active' : '');
                dot.onclick = () => goToSlide(i);
                navContainer.appendChild(dot);
            }
            updateSlide();
        }

        function updateSlide() {
            const slides = document.querySelectorAll('.slide');
            const progressBar = document.getElementById('progressBar');
            const currentSlideEl = document.getElementById('currentSlideNum');

            slides.forEach((slide, index) => {
                slide.classList.remove('active');
                if (index + 1 === currentSlide) {
                    setTimeout(() => slide.classList.add('active'), 50);
                }
            });

            const dots = document.querySelectorAll('.nav-btn');
            dots.forEach((dot, index) => {
                dot.classList.toggle('active', index + 1 === currentSlide);
            });

            const progress = (currentSlide / totalSlides) * 100;
            progressBar.style.width = progress + '%';
            currentSlideEl.textContent = currentSlide;
        }

        function nextSlide() {
            if (currentSlide < totalSlides) {
                currentSlide++;
                updateSlide();
            }
        }

        function prevSlide() {
            if (currentSlide > 1) {
                currentSlide--;
                updateSlide();
            }
        }

        function goToSlide(n) {
            currentSlide = n;
            updateSlide();
        }

        document.addEventListener('keydown', (e) => {
            if (e.key === 'ArrowRight' || e.key === ' ') {
                e.preventDefault();
                nextSlide();
            } else if (e.key === 'ArrowLeft') {
                e.preventDefault();
                prevSlide();
            } else if (e.key === 'Home') {
                e.preventDefault();
                goToSlide(1);
            } else if (e.key === 'End') {
                e.preventDefault();
                goToSlide(totalSlides);
            }
        });

        let touchStartX = 0;
        let touchEndX = 0;

        document.addEventListener('touchstart', e => {
            touchStartX = e.changedTouches[0].screenX;
        });

        document.addEventListener('touchend', e => {
            touchEndX = e.changedTouches[0].screenX;
            handleSwipe();
        });

        function handleSwipe() {
            if (touchEndX < touchStartX - 50) nextSlide();
            if (touchEndX > touchStartX + 50) prevSlide();
        }

        document.addEventListener('DOMContentLoaded', init);
    </script>
</body>
</html>
