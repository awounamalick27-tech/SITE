<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Maison Intelligente - Groupe 7 IUT FV Bandjoun</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700&family=Montserrat:wght@700;800&family=Orbitron:wght@400;500;700&display=swap" rel="stylesheet">
    <style>
        :root {
            --primary-dark: #0a0a1a;
            --primary-blue: #1a237e;
            --accent-blue: #2962ff;
            --accent-red: #d32f2f;
            --light-blue: #bbdefb;
            --cyber-blue: #00e5ff;
            --cyber-red: #ff1744;
            --text-light: #e3f2fd;
            --card-bg: rgba(26, 35, 126, 0.2);
            --border-glow: rgba(41, 98, 255, 0.5);
            --shadow: 0 10px 30px rgba(0, 0, 0, 0.5);
            --transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Poppins', sans-serif;
            line-height: 1.7;
            color: var(--text-light);
            background: linear-gradient(135deg, var(--primary-dark) 0%, var(--primary-blue) 70%);
            overflow-x: hidden;
            min-height: 100vh;
        }

        body::before {
            content: '';
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: 
                radial-gradient(circle at 20% 80%, rgba(41, 98, 255, 0.1) 0%, transparent 50%),
                radial-gradient(circle at 80% 20%, rgba(211, 47, 47, 0.1) 0%, transparent 50%);
            z-index: -1;
        }

        .container {
            width: 90%;
            max-width: 1300px;
            margin: 0 auto;
            padding: 0 20px;
        }

        /* Header */
        header {
            background: linear-gradient(135deg, rgba(10, 10, 26, 0.9) 0%, rgba(26, 35, 126, 0.9) 100%);
            padding: 4rem 0 3rem;
            text-align: center;
            border-bottom: 3px solid var(--accent-red);
            margin-bottom: 3rem;
            position: relative;
            overflow: hidden;
        }

        .cyber-grid {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-image: 
                linear-gradient(rgba(41, 98, 255, 0.1) 1px, transparent 1px),
                linear-gradient(90deg, rgba(41, 98, 255, 0.1) 1px, transparent 1px);
            background-size: 50px 50px;
            z-index: 0;
        }

        .theme-main {
            font-size: 4rem;
            font-family: 'Orbitron', sans-serif;
            background: linear-gradient(90deg, var(--cyber-blue), var(--accent-blue));
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
            margin-bottom: 0.5rem;
            text-shadow: 0 0 20px rgba(0, 229, 255, 0.5);
            letter-spacing: 2px;
            position: relative;
            z-index: 1;
        }

        .group-info {
            font-size: 2rem;
            color: var(--light-blue);
            margin-bottom: 1rem;
            position: relative;
            z-index: 1;
        }

        .institution {
            font-size: 1.3rem;
            color: var(--accent-red);
            background: rgba(0, 0, 0, 0.6);
            padding: 0.5rem 1.5rem;
            border-radius: 30px;
            display: inline-block;
            position: relative;
            z-index: 1;
            border: 1px solid var(--accent-red);
            box-shadow: 0 0 15px rgba(211, 47, 47, 0.3);
        }

        /* Sections */
        .section-title {
            text-align: center;
            font-size: 2.5rem;
            margin: 4rem 0 3rem;
            padding-bottom: 1rem;
            position: relative;
            font-family: 'Orbitron', sans-serif;
        }

        .section-title::after {
            content: '';
            position: absolute;
            bottom: 0;
            left: 50%;
            transform: translateX(-50%);
            width: 100px;
            height: 4px;
            background: linear-gradient(90deg, var(--accent-red), var(--accent-blue));
            border-radius: 2px;
        }

        /* Responsables Grid - 4 cartes */
        .responsables-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 2rem;
            margin-bottom: 4rem;
        }

        .card {
            background: var(--card-bg);
            border-radius: 15px;
            overflow: hidden;
            box-shadow: var(--shadow);
            transition: var(--transition);
            border: 1px solid var(--border-glow);
            backdrop-filter: blur(10px);
            position: relative;
        }

        .card::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: linear-gradient(45deg, transparent, rgba(255, 255, 255, 0.05), transparent);
            transform: translateX(-100%);
        }

        .card:hover::before {
            animation: shine 1.5s;
        }

        .card:hover {
            transform: translateY(-10px);
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.6);
            border-color: var(--cyber-blue);
        }

        .card-image {
            height: 250px;
            background: linear-gradient(135deg, rgba(26, 35, 126, 0.8), rgba(10, 10, 26, 0.9));
            display: flex;
            align-items: center;
            justify-content: center;
            position: relative;
            overflow: hidden;
            cursor: pointer;
        }

        .card-image img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            transition: transform 0.5s ease;
        }

        .card:hover .card-image img {
            transform: scale(1.05);
        }

        .image-overlay {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.7);
            display: flex;
            align-items: center;
            justify-content: center;
            opacity: 0;
            transition: opacity 0.3s;
        }

        .card-image:hover .image-overlay {
            opacity: 1;
        }

        .upload-btn {
            background: var(--cyber-blue);
            color: var(--primary-dark);
            border: none;
            padding: 10px 20px;
            border-radius: 20px;
            cursor: pointer;
            font-weight: 600;
            display: flex;
            align-items: center;
            gap: 8px;
            transition: var(--transition);
        }

        .upload-btn:hover {
            background: var(--cyber-red);
            color: white;
            transform: scale(1.1);
        }

        .card-content {
            padding: 1.5rem;
        }

        .card-content h3 {
            color: white;
            font-size: 1.5rem;
            margin-bottom: 0.5rem;
        }

        .role {
            color: var(--accent-red);
            font-weight: 600;
            margin-bottom: 1rem;
            font-size: 1.1rem;
            display: flex;
            align-items: center;
            gap: 8px;
        }

        .role i {
            color: var(--cyber-blue);
        }

        .card-content p {
            color: var(--light-blue);
            font-size: 0.95rem;
            line-height: 1.6;
        }

        /* Membres Grid */
        .membres-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 1.8rem;
            margin: 3rem 0;
        }

        .membre-card {
            background: var(--card-bg);
            border-radius: 15px;
            overflow: hidden;
            box-shadow: var(--shadow);
            transition: var(--transition);
            border: 1px solid var(--border-glow);
        }

        .membre-card:hover {
            transform: translateY(-8px);
            border-color: var(--cyber-blue);
        }

        .membre-photo {
            height: 200px;
            background: linear-gradient(135deg, rgba(26, 35, 126, 0.8), rgba(10, 10, 26, 0.9));
            display: flex;
            align-items: center;
            justify-content: center;
            position: relative;
            overflow: hidden;
            cursor: pointer;
        }

        .membre-photo img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }

        .membre-info {
            padding: 1.2rem;
            text-align: center;
        }

        .membre-info h4 {
            color: white;
            font-size: 1.2rem;
            margin-bottom: 0.5rem;
        }

        .membre-info p {
            color: var(--light-blue);
            font-size: 0.9rem;
            line-height: 1.5;
        }

        /* Features Grid */
        .features-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 2rem;
            margin: 3rem 0;
        }

        .feature-card {
            background: var(--card-bg);
            border-radius: 15px;
            overflow: hidden;
            box-shadow: var(--shadow);
            transition: var(--transition);
            border: 1px solid var(--border-glow);
            cursor: pointer;
        }

        .feature-card:hover {
            transform: translateY(-10px);
            border-color: var(--cyber-blue);
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.6);
        }

        .feature-image {
            height: 200px;
            background: linear-gradient(135deg, rgba(26, 35, 126, 0.8), rgba(10, 10, 26, 0.9));
            display: flex;
            align-items: center;
            justify-content: center;
            position: relative;
            overflow: hidden;
            cursor: pointer;
        }

        .feature-image img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }

        .feature-content {
            padding: 1.5rem;
        }

        .feature-content h3 {
            color: white;
            font-size: 1.4rem;
            margin-bottom: 1rem;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .feature-content h3 i {
            color: var(--accent-red);
            font-size: 1.2rem;
        }

        .feature-content p {
            color: var(--light-blue);
            font-size: 0.95rem;
            margin-bottom: 1rem;
        }

        .view-btn {
            background: linear-gradient(135deg, var(--accent-blue), var(--primary-blue));
            color: white;
            border: none;
            padding: 8px 16px;
            border-radius: 5px;
            cursor: pointer;
            transition: var(--transition);
            font-size: 0.9rem;
            display: flex;
            align-items: center;
            gap: 8px;
        }

        .view-btn:hover {
            background: linear-gradient(135deg, var(--cyber-blue), var(--accent-blue));
            transform: translateX(5px);
        }

        /* Contact Section */
        .contact-section {
            margin: 5rem 0 3rem;
            padding: 3rem;
            background: rgba(10, 10, 26, 0.6);
            border-radius: 20px;
            border: 1px solid var(--border-glow);
            position: relative;
            overflow: hidden;
        }

        .contact-section::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 5px;
            background: linear-gradient(90deg, var(--cyber-blue), var(--cyber-red), var(--accent-blue));
        }

        .contact-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 2rem;
            margin-top: 2rem;
        }

        .contact-item {
            text-align: center;
            padding: 2rem;
            background: rgba(26, 35, 126, 0.3);
            border-radius: 15px;
            transition: var(--transition);
            border: 1px solid transparent;
        }

        .contact-item:hover {
            background: rgba(26, 35, 126, 0.5);
            transform: translateY(-5px);
            border-color: var(--cyber-blue);
        }

        .contact-icon {
            font-size: 2.5rem;
            color: var(--cyber-blue);
            margin-bottom: 1rem;
            transition: var(--transition);
        }

        .contact-item:hover .contact-icon {
            color: var(--cyber-red);
            transform: scale(1.2);
        }

        .contact-item h4 {
            color: white;
            margin-bottom: 1rem;
            font-size: 1.3rem;
        }

        .contact-info {
            color: var(--light-blue);
            font-size: 1.1rem;
        }

        .contact-info a {
            color: var(--cyber-blue);
            text-decoration: none;
            transition: var(--transition);
        }

        .contact-info a:hover {
            color: var(--cyber-red);
            text-decoration: underline;
        }

        /* Footer */
        footer {
            background: rgba(5, 5, 15, 0.9);
            padding: 3rem 0;
            text-align: center;
            margin-top: 4rem;
            border-top: 2px solid var(--accent-red);
        }

        /* Modal */
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.9);
            z-index: 1000;
            justify-content: center;
            align-items: center;
            padding: 20px;
        }

        .modal-content {
            background: linear-gradient(135deg, rgba(10, 10, 26, 0.95), rgba(26, 35, 126, 0.95));
            border-radius: 20px;
            width: 90%;
            max-width: 800px;
            max-height: 90vh;
            overflow-y: auto;
            padding: 2rem;
            position: relative;
            border: 2px solid var(--cyber-blue);
            box-shadow: 0 0 40px rgba(0, 229, 255, 0.3);
        }

        .close-modal {
            position: absolute;
            top: 1rem;
            right: 1rem;
            background: var(--accent-red);
            color: white;
            border: none;
            border-radius: 50%;
            width: 40px;
            height: 40px;
            font-size: 1.5rem;
            cursor: pointer;
            transition: var(--transition);
        }

        .close-modal:hover {
            background: #b71c1c;
            transform: rotate(90deg);
        }

        .modal-image {
            width: 100%;
            height: 300px;
            background: linear-gradient(135deg, rgba(26, 35, 126, 0.8), rgba(10, 10, 26, 0.9));
            border-radius: 10px;
            margin-bottom: 2rem;
            overflow: hidden;
        }

        .modal-image img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }

        /* Edit Mode */
        .edit-btn {
            position: fixed;
            bottom: 30px;
            right: 30px;
            background: linear-gradient(135deg, var(--accent-red), #b71c1c);
            color: white;
            border: none;
            border-radius: 50px;
            padding: 15px 25px;
            font-size: 1.1rem;
            cursor: pointer;
            z-index: 100;
            display: flex;
            align-items: center;
            gap: 10px;
            box-shadow: 0 8px 25px rgba(211, 47, 47, 0.4);
            transition: var(--transition);
        }

        .edit-btn:hover {
            transform: translateY(-5px) scale(1.05);
            box-shadow: 0 12px 30px rgba(211, 47, 47, 0.6);
        }

        .editable {
            position: relative;
            cursor: pointer;
            transition: all 0.3s;
        }

        .editable:hover {
            outline: 2px dashed var(--cyber-blue);
            outline-offset: 5px;
            background: rgba(41, 98, 255, 0.1);
        }

        .edit-tools {
            position: fixed;
            top: 50%;
            right: 20px;
            transform: translateY(-50%);
            background: rgba(10, 10, 26, 0.95);
            border: 2px solid var(--cyber-blue);
            border-radius: 10px;
            padding: 1rem;
            z-index: 101;
            display: none;
            flex-direction: column;
            gap: 10px;
            min-width: 200px;
            backdrop-filter: blur(10px);
        }

        .edit-tools.active {
            display: flex;
            animation: slideIn 0.4s ease-out;
        }

        .edit-tools button {
            background: linear-gradient(135deg, var(--accent-blue), var(--primary-blue));
            color: white;
            border: none;
            padding: 12px 15px;
            border-radius: 8px;
            cursor: pointer;
            transition: var(--transition);
            font-size: 1rem;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 10px;
        }

        .edit-tools button:hover {
            background: linear-gradient(135deg, var(--cyber-blue), var(--accent-blue));
            transform: translateX(-5px);
        }

        /* Animations */
        @keyframes shine {
            0% { transform: translateX(-100%); }
            100% { transform: translateX(100%); }
        }

        @keyframes slideIn {
            from { opacity: 0; transform: translate(100px, -50%); }
            to { opacity: 1; transform: translate(0, -50%); }
        }

        /* Notification */
        .notification {
            position: fixed;
            top: 20px;
            right: 20px;
            padding: 15px 20px;
            border-radius: 10px;
            color: white;
            font-weight: 600;
            z-index: 10000;
            display: flex;
            align-items: center;
            gap: 15px;
            animation: slideInRight 0.3s ease-out;
            max-width: 350px;
            box-shadow: 0 5px 20px rgba(0,0,0,0.3);
        }

        .notification-success {
            background: linear-gradient(135deg, #2e7d32, #1b5e20);
        }

        .notification-error {
            background: linear-gradient(135deg, #c62828, #b71c1c);
        }

        .notification-warning {
            background: linear-gradient(135deg, #f57c00, #e65100);
        }

        .notification-info {
            background: linear-gradient(135deg, var(--accent-blue), var(--primary-blue));
        }

        @keyframes slideInRight {
            from { transform: translateX(100%); opacity: 0; }
            to { transform: translateX(0); opacity: 1; }
        }

        @keyframes slideOutRight {
            from { transform: translateX(0); opacity: 1; }
            to { transform: translateX(100%); opacity: 0; }
        }

        /* Responsive */
        @media (max-width: 1100px) {
            .responsables-grid {
                grid-template-columns: repeat(2, 1fr);
            }
        }

        @media (max-width: 768px) {
            .theme-main {
                font-size: 2.5rem;
            }
            .group-info {
                font-size: 1.5rem;
            }
            .section-title {
                font-size: 2rem;
            }
            .responsables-grid,
            .membres-grid,
            .features-grid,
            .contact-grid {
                grid-template-columns: 1fr;
            }
            .edit-tools {
                top: auto;
                bottom: 100px;
                right: 10px;
                left: 10px;
                transform: none;
                flex-direction: row;
                flex-wrap: wrap;
                justify-content: center;
            }
            .edit-tools button {
                flex: 1;
                min-width: 140px;
                padding: 10px;
            }
        }

        @media (max-width: 480px) {
            .theme-main {
                font-size: 2rem;
            }
            .contact-section {
                padding: 2rem 1rem;
            }
        }
    </style>
</head>
<body>
    <!-- Header -->
    <header>
        <div class="cyber-grid"></div>
        <div class="container">
            <h1 class="theme-main" id="theme-title" data-editable="true">THÈME : MAISON INTELLIGENTE</h1>
            <p class="group-info" id="group-number" data-editable="true">GROUPE 7</p>
            <p class="institution" id="institution" data-editable="true">IUT FOTSO VICTOR DE BANDJOUN</p>
        </div>
    </header>

    <main class="container">
        <!-- Présentation des responsables (4 cartes) -->
        <section class="presentation-section">
            <h2 class="section-title" id="admin-title" data-editable="true">PRÉSENTATION DES RESPONSABLES</h2>
            
            <div class="responsables-grid">
                <!-- Carte 1 : Directeur -->
                <div class="card">
                    <div class="card-image" onclick="uploadImage('director-img')">
                        <img src="https://via.placeholder.com/400x250/1a237e/ffffff?text=DIRECTEUR+IUT" 
                             alt="Directeur IUT" 
                             id="director-img"
                             data-editable="true"
                             data-type="image">
                        <div class="image-overlay">
                            <button class="upload-btn">
                                <i class="fas fa-camera"></i> Changer photo
                            </button>
                        </div>
                    </div>
                    <div class="card-content">
                        <h3 id="director-name" data-editable="true">Directeur de l'IUT</h3>
                        <p class="role"><i class="fas fa-user-tie"></i> <span id="director-role" data-editable="true">Fotso Victor de Bandjoun</span></p>
                        <p id="director-desc" data-editable="true">Directeur de l'IUT Fotso Victor de Bandjoun, responsable de la supervision académique et administrative de l'institution.</p>
                    </div>
                </div>

                <!-- Carte 2 : Chef de département -->
                <div class="card">
                    <div class="card-image" onclick="uploadImage('chef-img')">
                        <img src="https://via.placeholder.com/400x250/2962ff/ffffff?text=CHEF+DÉPARTEMENT+GTR" 
                             alt="Chef Département GTR" 
                             id="chef-img"
                             data-editable="true"
                             data-type="image">
                        <div class="image-overlay">
                            <button class="upload-btn">
                                <i class="fas fa-camera"></i> Changer photo
                            </button>
                        </div>
                    </div>
                    <div class="card-content">
                        <h3 id="chef-name" data-editable="true">Chef de Département</h3>
                        <p class="role"><i class="fas fa-user-graduate"></i> <span id="chef-role" data-editable="true">Département GTR</span></p>
                        <p id="chef-desc" data-editable="true">Responsable du département Génie des Télécommunications et Réseaux (GTR), supervise les programmes pédagogiques.</p>
                    </div>
                </div>

                <!-- Carte 3 : Professeur (NOUVEAU) -->
                <div class="card">
                    <div class="card-image" onclick="uploadImage('professeur-img')">
                        <img src="https://via.placeholder.com/400x250/d32f2f/ffffff?text=PROFESSEUR+ENCOADRANT" 
                             alt="Professeur Encadrant" 
                             id="professeur-img"
                             data-editable="true"
                             data-type="image">
                        <div class="image-overlay">
                            <button class="upload-btn">
                                <i class="fas fa-camera"></i> Changer photo
                            </button>
                        </div>
                    </div>
                    <div class="card-content">
                        <h3 id="professeur-name" data-editable="true">Professeur Encadrant</h3>
                        <p class="role"><i class="fas fa-chalkboard-teacher"></i> <span id="professeur-role" data-editable="true">Professeur du Projet</span></p>
                        <p id="professeur-desc" data-editable="true">Professeur encadrant du projet, apporte son expertise et son soutien technique pour la réalisation du projet.</p>
                    </div>
                </div>

                <!-- Carte 4 : Délégué -->
                <div class="card">
                    <div class="card-image" onclick="uploadImage('delegue-img')">
                        <img src="https://via.placeholder.com/400x250/00e5ff/1a237e?text=DÉLÉGUÉ+LIRT" 
                             alt="Délégué LIRT" 
                             id="delegue-img"
                             data-editable="true"
                             data-type="image">
                        <div class="image-overlay">
                            <button class="upload-btn">
                                <i class="fas fa-camera"></i> Changer photo
                            </button>
                        </div>
                    </div>
                    <div class="card-content">
                        <h3 id="delegue-name" data-editable="true">Délégué</h3>
                        <p class="role"><i class="fas fa-user-friends"></i> <span id="delegue-role" data-editable="true">Délégué de LIRT</span></p>
                        <p id="delegue-desc" data-editable="true">Représentant élu des étudiants de la Licence en Informatique et Réseaux de Télécommunications.</p>
                    </div>
                </div>
            </div>
        </section>

        <!-- Membres du groupe -->
        <section class="members-section">
            <h2 class="section-title" id="members-title" data-editable="true">MEMBRES DU GROUPE 7</h2>
            <p style="text-align: center; color: var(--light-blue); margin-bottom: 2rem; font-size: 1.1rem;" 
               id="members-subtitle" 
               data-editable="true">
                Nous sommes 5 étudiants passionnés par l'innovation technologique et les systèmes intelligents.
            </p>
            
            <div class="membres-grid">
                <!-- Membre 1 : Ange Foting -->
                <div class="membre-card">
                    <div class="membre-photo" onclick="uploadImage('membre1-img')">
                        <img src="https://via.placeholder.com/300x200/1a237e/ffffff?text=ANGE+FOTING" 
                             alt="Ange Foting" 
                             id="membre1-img"
                             data-editable="true"
                             data-type="image">
                    </div>
                    <div class="membre-info">
                        <h4 id="membre1-name" data-editable="true">Ange Foting</h4>
                        <p id="membre1-desc" data-editable="true">Spécialiste en réseaux et sécurité. Responsable de la partie sécurité du projet.</p>
                    </div>
                </div>

                <!-- Membre 2 : Awouna Malick -->
                <div class="membre-card">
                    <div class="membre-photo" onclick="uploadImage('membre2-img')">
                        <img src="https://via.placeholder.com/300x200/2962ff/ffffff?text=AWOUN+MALICK" 
                             alt="Awouna Malick" 
                             id="membre2-img"
                             data-editable="true"
                             data-type="image">
                    </div>
                    <div class="membre-info">
                        <h4 id="membre2-name" data-editable="true">Awouna Malick</h4>
                        <p id="membre2-desc" data-editable="true">Expert en électronique et automatisme. Gère les systèmes de contrôle d'éclairage.</p>
                    </div>
                </div>

                <!-- Membre 3 : Simo Olivier -->
                <div class="membre-card">
                    <div class="membre-photo" onclick="uploadImage('membre3-img')">
                        <img src="https://via.placeholder.com/300x200/d32f2f/ffffff?text=SIMO+OLIVIER" 
                             alt="Simo Olivier" 
                             id="membre3-img"
                             data-editable="true"
                             data-type="image">
                    </div>
                    <div class="membre-info">
                        <h4 id="membre3-name" data-editable="true">Simo Olivier</h4>
                        <p id="membre3-desc" data-editable="true">Développeur IoT. En charge des interfaces de commande à distance.</p>
                    </div>
                </div>

                <!-- Membre 4 : Tuedem Michelle -->
                <div class="membre-card">
                    <div class="membre-photo" onclick="uploadImage('membre4-img')">
                        <img src="https://via.placeholder.com/300x200/1a237e/ffffff?text=TUEDEM+MICHELLE" 
                             alt="Tuedem Michelle" 
                             id="membre4-img"
                             data-editable="true"
                             data-type="image">
                    </div>
                    <div class="membre-info">
                        <h4 id="membre4-name" data-editable="true">Tuedem Michelle</h4>
                        <p id="membre4-desc" data-editable="true">Designer système. Conçoit l'expérience utilisateur et les interfaces.</p>
                    </div>
                </div>

                <!-- Membre 5 : Coordinateur -->
                <div class="membre-card">
                    <div class="membre-photo" onclick="uploadImage('membre5-img')">
                        <img src="https://via.placeholder.com/300x200/2962ff/ffffff?text=COORDINATEUR" 
                             alt="Coordinateur" 
                             id="membre5-img"
                             data-editable="true"
                             data-type="image">
                    </div>
                    <div class="membre-info">
                        <h4 id="membre5-name" data-editable="true">Membre 5</h4>
                        <p id="membre5-desc" data-editable="true">Coordinateur du projet. Assure la gestion et la communication du groupe.</p>
                    </div>
                </div>
            </div>
        </section>

        <!-- Maison Intelligente -->
        <section class="features-section">
            <h2 class="section-title" id="features-title" data-editable="true">MAISON INTELLIGENTE</h2>
            <p style="text-align: center; color: var(--light-blue); margin-bottom: 2rem; font-size: 1.1rem;" 
               id="features-subtitle" 
               data-editable="true">
                Découvrez les fonctionnalités innovantes de notre projet de maison intelligente.
            </p>
            
            <div class="features-grid">
                <!-- Sécurité -->
                <div class="feature-card" data-feature="security">
                    <div class="feature-image" onclick="uploadImage('security-img')">
                        <img src="https://via.placeholder.com/400x200/1a237e/ffffff?text=SÉCURITÉ+ACCÈS" 
                             alt="Sécurité" 
                             id="security-img"
                             data-editable="true"
                             data-type="image">
                    </div>
                    <div class="feature-content">
                        <h3><i class="fas fa-shield-alt"></i> <span id="security-title" data-editable="true">Sécurité pour l'accès au domicile</span></h3>
                        <p id="security-desc" data-editable="true">Système de sécurité avancé avec reconnaissance faciale et empreintes digitales pour un accès sécurisé.</p>
                        <button class="view-btn" onclick="openModal('security-modal')">
                            <i class="fas fa-eye"></i> Voir détails
                        </button>
                    </div>
                </div>

                <!-- Séchoir -->
                <div class="feature-card" data-feature="dryer">
                    <div class="feature-image" onclick="uploadImage('dryer-img')">
                        <img src="https://via.placeholder.com/400x200/2962ff/ffffff?text=SÉCHOIR+INTELLIGENT" 
                             alt="Séchoir Intelligent" 
                             id="dryer-img"
                             data-editable="true"
                             data-type="image">
                    </div>
                    <div class="feature-content">
                        <h3><i class="fas fa-wind"></i> <span id="dryer-title" data-editable="true">Séchoir Intelligent</span></h3>
                        <p id="dryer-desc" data-editable="true">Séchoir équipé de capteurs qui ajuste automatiquement le temps de séchage selon le type de tissu.</p>
                        <button class="view-btn" onclick="openModal('dryer-modal')">
                            <i class="fas fa-eye"></i> Voir détails
                        </button>
                    </div>
                </div>

                <!-- Interrupteur -->
                <div class="feature-card" data-feature="switch">
                    <div class="feature-image" onclick="uploadImage('switch-img')">
                        <img src="https://via.placeholder.com/400x200/d32f2f/ffffff?text=INTERRUPTEUR+CRÉPUSCULAIRE" 
                             alt="Interrupteur" 
                             id="switch-img"
                             data-editable="true"
                             data-type="image">
                    </div>
                    <div class="feature-content">
                        <h3><i class="fas fa-lightbulb"></i> <span id="switch-title" data-editable="true">Interrupteur Crépusculaire</span></h3>
                        <p id="switch-desc" data-editable="true">Système d'éclairage automatique qui s'active au crépuscule et s'éteint à l'aube.</p>
                        <button class="view-btn" onclick="openModal('switch-modal')">
                            <i class="fas fa-eye"></i> Voir détails
                        </button>
                    </div>
                </div>

                <!-- WiFi -->
                <div class="feature-card" data-feature="wifi">
                    <div class="feature-image" onclick="uploadImage('wifi-img')">
                        <img src="https://via.placeholder.com/400x200/1a237e/ffffff?text=COMMANDE+WiFi" 
                             alt="Commande WiFi" 
                             id="wifi-img"
                             data-editable="true"
                             data-type="image">
                    </div>
                    <div class="feature-content">
                        <h3><i class="fas fa-wifi"></i> <span id="wifi-title" data-editable="true">Commande d'Ampoule par WiFi</span></h3>
                        <p id="wifi-desc" data-editable="true">Contrôle à distance des ampoules connectées via application mobile avec programmation horaire.</p>
                        <button class="view-btn" onclick="openModal('wifi-modal')">
                            <i class="fas fa-eye"></i> Voir détails
                        </button>
                    </div>
                </div>
            </div>
        </section>

        <!-- Contact -->
        <section class="contact-section">
            <h2 class="section-title" id="contact-title" data-editable="true">CONTACTER NOUS</h2>
            <p style="text-align: center; color: var(--light-blue); margin-bottom: 2rem; font-size: 1.1rem;" 
               id="contact-subtitle" 
               data-editable="true">
                Pour plus d'informations sur notre projet ou pour collaborer avec nous, n'hésitez pas à nous contacter.
            </p>
            
            <div class="contact-grid">
                <div class="contact-item">
                    <div class="contact-icon">
                        <i class="fas fa-envelope"></i>
                    </div>
                    <h4 id="email-title" data-editable="true">Email</h4>
                    <p class="contact-info" id="email-value" data-editable="true">
                        <a href="mailto:awounamalick27@gmail.com">awounamalick27@gmail.com</a>
                    </p>
                </div>

                <div class="contact-item">
                    <div class="contact-icon">
                        <i class="fab fa-whatsapp"></i>
                    </div>
                    <h4 id="whatsapp-title" data-editable="true">WhatsApp</h4>
                    <p class="contact-info" id="whatsapp-value" data-editable="true">
                        <a href="https://wa.me/237654183011" target="_blank">+237 654 183 011</a>
                    </p>
                </div>

                <div class="contact-item">
                    <div class="contact-icon">
                        <i class="fas fa-university"></i>
                    </div>
                    <h4 id="school-title" data-editable="true">École</h4>
                    <p class="contact-info" id="school-value" data-editable="true">IUT FOTSO VICTOR DE BANDJOUN</p>
                </div>
            </div>
        </section>
    </main>

    <!-- Footer -->
    <footer>
        <div class="container">
            <p id="footer-text" data-editable="true">© 2024 - Projet Maison Intelligente - Groupe 7 - IUT Fotso Victor de Bandjoun</p>
        </div>
    </footer>

    <!-- Modals -->
    <div id="security-modal" class="modal">
        <div class="modal-content">
            <button class="close-modal" onclick="closeModal('security-modal')">&times;</button>
            <h2 id="modal-security-title" data-editable="true">Sécurité pour l'accès au domicile</h2>
            <div class="modal-image" onclick="uploadImage('modal-security-img')">
                <img src="https://via.placeholder.com/800x400/1a237e/ffffff?text=SÉCURITÉ+DÉTAILS" 
                     alt="Sécurité Détails" 
                     id="modal-security-img"
                     data-editable="true"
                     data-type="image">
            </div>
            <div id="modal-security-desc" data-editable="true">
                <p>Notre système de sécurité pour l'accès au domicile intègre plusieurs technologies d'authentification pour assurer une protection maximale :</p>
                <ul style="margin: 1rem 0; padding-left: 1.5rem;">
                    <li><strong>Reconnaissance faciale :</strong> Utilisation d'une caméra avec intelligence artificielle pour identifier les résidents autorisés.</li>
                    <li><strong>Empreintes digitales :</strong> Capteur biométrique pour une authentification rapide et sécurisée.</li>
                    <li><strong>Code PIN :</strong> Système de code numérique de secours avec limitation des tentatives.</li>
                    <li><strong>Notification en temps réel :</strong> Envoi d'alertes sur smartphone en cas de tentative d'intrusion.</li>
                    <li><strong>Journal d'accès :</strong> Historique complet de toutes les entrées et sorties avec horodatage.</li>
                </ul>
            </div>
        </div>
    </div>

    <div id="dryer-modal" class="modal">
        <div class="modal-content">
            <button class="close-modal" onclick="closeModal('dryer-modal')">&times;</button>
            <h2 id="modal-dryer-title" data-editable="true">Séchoir Intelligent</h2>
            <div class="modal-image" onclick="uploadImage('modal-dryer-img')">
                <img src="https://via.placeholder.com/800x400/2962ff/ffffff?text=SÉCHOIR+DÉTAILS" 
                     alt="Séchoir Détails" 
                     id="modal-dryer-img"
                     data-editable="true"
                     data-type="image">
            </div>
            <div id="modal-dryer-desc" data-editable="true">
                <p>Le séchoir intelligent utilise des capteurs et l'intelligence artificielle pour optimiser le processus de séchage du linge :</p>
                <ul style="margin: 1rem 0; padding-left: 1.5rem;">
                    <li><strong>Détection automatique du type de tissu :</strong> Le système identifie le type de tissu et ajuste la température et la durée de séchage en conséquence.</li>
                    <li><strong>Capteurs d'humidité :</strong> Mesure en continu l'humidité du linge pour arrêter le séchage dès que le niveau optimal est atteint.</li>
                    <li><strong>Économie d'énergie :</strong> Réduction de la consommation d'énergie de jusqu'à 30% par rapport aux séchoirs traditionnels.</li>
                    <li><strong>Notifications :</strong> Alerte sur smartphone lorsque le linge est sec ou en cas de problème.</li>
                    <li><strong>Programmation :</strong> Possibilité de programmer le séchage pour des heures creuses (tarifs électriques réduits).</li>
                </ul>
            </div>
        </div>
    </div>

    <div id="switch-modal" class="modal">
        <div class="modal-content">
            <button class="close-modal" onclick="closeModal('switch-modal')">&times;</button>
            <h2 id="modal-switch-title" data-editable="true">Interrupteur Crépusculaire</h2>
            <div class="modal-image" onclick="uploadImage('modal-switch-img')">
                <img src="https://via.placeholder.com/800x400/d32f2f/ffffff?text=INTERRUPTEUR+DÉTAILS" 
                     alt="Interrupteur Détails" 
                     id="modal-switch-img"
                     data-editable="true"
                     data-type="image">
            </div>
            <div id="modal-switch-desc" data-editable="true">
                <p>L'interrupteur crépusculaire automatise l'éclairage extérieur en fonction de la luminosité ambiante :</p>
                <ul style="margin: 1rem 0; padding-left: 1.5rem;">
                    <li><strong>Détection de luminosité :</strong> Capteur photoélectrique qui mesure l'intensité lumineuse pour déclencher l'allumage au crépuscule.</li>
                    <li><strong>Détection de mouvement :</strong> Activation supplémentaire par détection de présence pour économie d'énergie.</li>
                    <li><strong>Programmation horaire :</strong> Possibilité de définir des plages horaires spécifiques pour l'activation.</li>
                    <li><strong>Mode vacances :</strong> Simulation de présence en allumant aléatoirement les lumières pendant l'absence des occupants.</li>
                    <li><strong>Intégration solaire :</strong> Option avec panneau solaire intégré pour une autonomie énergétique complète.</li>
                </ul>
            </div>
        </div>
    </div>

    <div id="wifi-modal" class="modal">
        <div class="modal-content">
            <button class="close-modal" onclick="closeModal('wifi-modal')">&times;</button>
            <h2 id="modal-wifi-title" data-editable="true">Commande d'Ampoule par WiFi</h2>
            <div class="modal-image" onclick="uploadImage('modal-wifi-img')">
                <img src="https://via.placeholder.com/800x400/1a237e/ffffff?text=WiFi+DÉTAILS" 
                     alt="WiFi Détails" 
                     id="modal-wifi-img"
                     data-editable="true"
                     data-type="image">
            </div>
            <div id="modal-wifi-desc" data-editable="true">
                <p>Notre système de commande d'ampoules par WiFi permet un contrôle complet de l'éclairage domestique depuis un smartphone ou une tablette :</p>
                <ul style="margin: 1rem 0; padding-left: 1.5rem;">
                    <li><strong>Contrôle à distance :</strong> Allumer/éteindre et dimmer les lumières depuis n'importe où avec une connexion Internet.</li>
                    <li><strong>Scénarios d'éclairage :</strong> Création de scènes prédéfinies (cinéma, dîner, lecture) avec ajustement automatique de plusieurs ampoules.</li>
                    <li><strong>Programmation :</strong> Planification d'allumage/extinction selon des horaires ou des événements (lever/coucher du soleil).</li>
                    <li><strong>Intégration vocale :</strong> Compatible avec les assistants vocaux (Google Assistant, Amazon Alexa).</li>
                    <li><strong>Suivi de consommation :</strong> Monitoring en temps réel de la consommation énergétique de chaque ampoule.</li>
                </ul>
            </div>
        </div>
    </div>

    <!-- Edit Button -->
    <button class="edit-btn" id="edit-toggle">
        <i class="fas fa-edit"></i> Mode Édition
    </button>

    <div class="edit-tools" id="edit-tools">
        <button id="edit-text-btn">
            <i class="fas fa-font"></i> Modifier texte
        </button>
        <button id="edit-image-btn">
            <i class="fas fa-image"></i> Changer image
        </button>
        <button id="save-btn">
            <i class="fas fa-save"></i> Sauvegarder
        </button>
        <button id="reset-btn">
            <i class="fas fa-redo"></i> Réinitialiser
        </button>
        <button id="export-btn">
            <i class="fas fa-download"></i> Exporter
        </button>
        <button id="import-btn">
            <i class="fas fa-upload"></i> Importer
        </button>
    </div>

    <!-- File Input (hidden) -->
    <input type="file" id="file-input" accept="image/*" style="display: none;">

    <script>
        // Variables globales
        let editMode = false;
        let currentEditable = null;
        let savedData = {};

        // Charger les données sauvegardées
        function loadSavedData() {
            const data = localStorage.getItem('maison_intelligente_data');
            if (data) {
                savedData = JSON.parse(data);
                applySavedData();
                showNotification('✅ Données chargées depuis le stockage local', 'success');
            }
        }

        // Appliquer les données sauvegardées
        function applySavedData() {
            Object.keys(savedData).forEach(id => {
                const element = document.getElementById(id);
                if (element) {
                    if (element.getAttribute('data-type') === 'image') {
                        element.src = savedData[id];
                    } else {
                        element.innerHTML = savedData[id];
                    }
                }
            });
        }

        // Sauvegarder toutes les données
        function saveAllData() {
            const data = {};
            document.querySelectorAll('[data-editable="true"]').forEach(el => {
                if (el.getAttribute('data-type') === 'image') {
                    data[el.id] = el.src;
                } else {
                    data[el.id] = el.innerHTML;
                }
            });
            
            localStorage.setItem('maison_intelligente_data', JSON.stringify(data));
            savedData = data;
            
            showNotification('✅ Modifications sauvegardées !', 'success');
        }

        // Upload d'image
        function uploadImage(imageId) {
            if (!editMode) {
                showNotification('⚠️ Activez d\'abord le mode édition', 'warning');
                return;
            }
            
            const input = document.createElement('input');
            input.type = 'file';
            input.accept = 'image/*';
            
            input.onchange = function(event) {
                const file = event.target.files[0];
                if (file) {
                    // Vérifier la taille du fichier (max 5MB)
                    if (file.size > 5 * 1024 * 1024) {
                        showNotification('❌ L\'image est trop volumineuse (max 5MB)', 'error');
                        return;
                    }
                    
                    const reader = new FileReader();
                    reader.onload = function(e) {
                        const img = document.getElementById(imageId);
                        if (img) {
                            img.src = e.target.result;
                            saveElementData(imageId, e.target.result);
                            showNotification('✅ Image mise à jour avec succès !', 'success');
                        }
                    };
                    reader.readAsDataURL(file);
                }
            };
            
            input.click();
        }

        // Sauvegarder un élément individuel
        function saveElementData(id, content) {
            savedData[id] = content;
            localStorage.setItem('maison_intelligente_data', JSON.stringify(savedData));
        }

        // Activer/désactiver le mode édition
        document.getElementById('edit-toggle').addEventListener('click', function() {
            editMode = !editMode;
            const editables = document.querySelectorAll('[data-editable="true"]');
            const editTools = document.getElementById('edit-tools');
            
            if (editMode) {
                // Activer le mode édition
                this.innerHTML = '<i class="fas fa-times"></i> Quitter Édition';
                this.style.background = 'linear-gradient(135deg, #b71c1c, var(--accent-red))';
                editTools.classList.add('active');
                
                editables.forEach(el => {
                    el.classList.add('editable');
                    if (el.getAttribute('data-type') !== 'image') {
                        el.addEventListener('click', handleEditClick);
                    }
                });
                
                showNotification('✏️ Mode édition activé - Cliquez sur les éléments pour les modifier', 'info');
            } else {
                // Désactiver le mode édition
                this.innerHTML = '<i class="fas fa-edit"></i> Mode Édition';
                this.style.background = 'linear-gradient(135deg, var(--accent-red), #b71c1c)';
                editTools.classList.remove('active');
                
                editables.forEach(el => {
                    el.classList.remove('editable');
                    if (el.getAttribute('data-type') !== 'image') {
                        el.removeEventListener('click', handleEditClick);
                    }
                });
                
                if (currentEditable) {
                    currentEditable.contentEditable = false;
                    currentEditable = null;
                }
                
                saveAllData();
            }
        });

        // Gérer les clics sur les éléments texte éditables
        function handleEditClick(e) {
            if (!editMode) return;
            
            e.stopPropagation();
            currentEditable = this;
            
            // Permettre l'édition de texte
            this.contentEditable = true;
            this.focus();
            
            // Sélectionner tout le texte
            const range = document.createRange();
            range.selectNodeContents(this);
            const selection = window.getSelection();
            selection.removeAllRanges();
            selection.addRange(range);
        }

        // Boutons de la barre d'outils
        document.getElementById('edit-text-btn').addEventListener('click', function() {
            if (currentEditable && currentEditable.getAttribute('data-type') !== 'image') {
                currentEditable.contentEditable = true;
                currentEditable.focus();
            } else {
                showNotification('⚠️ Veuillez d\'abord cliquer sur un texte à éditer', 'warning');
            }
        });

        document.getElementById('edit-image-btn').addEventListener('click', function() {
            if (currentEditable && currentEditable.getAttribute('data-type') === 'image') {
                uploadImage(currentEditable.id);
            } else {
                showNotification('⚠️ Veuillez d\'abord cliquer sur une image à changer', 'warning');
            }
        });

        document.getElementById('save-btn').addEventListener('click', saveAllData);

        document.getElementById('reset-btn').addEventListener('click', function() {
            if (confirm('⚠️ Voulez-vous vraiment réinitialiser toutes les modifications ?')) {
                localStorage.removeItem('maison_intelligente_data');
                location.reload();
            }
        });

        document.getElementById('export-btn').addEventListener('click', function() {
            const dataStr = JSON.stringify(savedData, null, 2);
            const dataUri = 'data:application/json;charset=utf-8,'+ encodeURIComponent(dataStr);
            
            const exportFileDefaultName = 'maison_intelligente_backup.json';
            
            const linkElement = document.createElement('a');
            linkElement.setAttribute('href', dataUri);
            linkElement.setAttribute('download', exportFileDefaultName);
            linkElement.click();
            
            showNotification('📥 Données exportées avec succès !', 'success');
        });

        document.getElementById('import-btn').addEventListener('click', function() {
            const input = document.createElement('input');
            input.type = 'file';
            input.accept = '.json';
            
            input.onchange = function(event) {
                const file = event.target.files[0];
                if (file) {
                    const reader = new FileReader();
                    reader.onload = function(e) {
                        try {
                            const importedData = JSON.parse(e.target.result);
                            localStorage.setItem('maison_intelligente_data', JSON.stringify(importedData));
                            showNotification('✅ Données importées avec succès ! Rechargement...', 'success');
                            setTimeout(() => location.reload(), 1500);
                        } catch (error) {
                            showNotification('❌ Erreur lors de l\'import des données', 'error');
                            console.error('Erreur import:', error);
                        }
                    };
                    reader.readAsText(file);
                }
            };
            
            input.click();
        });

        // Gérer les modals
        function openModal(modalId) {
            if (editMode) return; // Ne pas ouvrir les modals en mode édition
            document.getElementById(modalId).style.display = 'flex';
        }

        function closeModal(modalId) {
            document.getElementById(modalId).style.display = 'none';
        }

        // Fermer les modals avec Escape
        document.addEventListener('keydown', function(e) {
            if (e.key === 'Escape') {
                document.querySelectorAll('.modal').forEach(modal => {
                    modal.style.display = 'none';
                });
            }
        });

        // Gérer la fin de l'édition de texte
        document.addEventListener('click', function(e) {
            if (editMode && currentEditable && !currentEditable.contains(e.target)) {
                if (currentEditable.getAttribute('data-type') !== 'image') {
                    currentEditable.contentEditable = false;
                    saveElementData(currentEditable.id, currentEditable.innerHTML);
                }
                currentEditable = null;
            }
        });

        // Sauvegarde automatique avec Ctrl+S
        document.addEventListener('keydown', function(e) {
            if ((e.ctrlKey || e.metaKey) && e.key === 's') {
                e.preventDefault();
                saveAllData();
            }
        });

        // Fonction de notification
        function showNotification(message, type) {
            // Supprimer l'ancienne notification
            const oldNotification = document.querySelector('.notification');
            if (oldNotification) {
                oldNotification.style.animation = 'slideOutRight 0.3s ease-out';
                setTimeout(() => oldNotification.remove(), 300);
            }
            
            // Créer la nouvelle notification
            const notification = document.createElement('div');
            notification.className = `notification notification-${type}`;
            notification.innerHTML = `
                <span>${message}</span>
                <button onclick="this.parentElement.remove()" style="background: none; border: none; color: white; font-size: 1.5rem; cursor: pointer; padding: 0; margin: 0; line-height: 1;">&times;</button>
            `;
            
            document.body.appendChild(notification);
            
            // Auto-remove après 4 secondes
            setTimeout(() => {
                if (notification.parentElement) {
                    notification.style.animation = 'slideOutRight 0.3s ease-out';
                    setTimeout(() => notification.remove(), 300);
                }
            }, 4000);
        }

        // Animation au scroll
        function animateOnScroll() {
            const cards = document.querySelectorAll('.card, .membre-card, .feature-card');
            cards.forEach(card => {
                const cardTop = card.getBoundingClientRect().top;
                const windowHeight = window.innerHeight;
                
                if (cardTop < windowHeight - 100) {
                    card.style.opacity = '1';
                    card.style.transform = 'translateY(0)';
                }
            });
        }

        // Initialiser les animations
        document.querySelectorAll('.card, .membre-card, .feature-card').forEach(card => {
            card.style.opacity = '0';
            card.style.transform = 'translateY(20px)';
            card.style.transition = 'opacity 0.6s ease, transform 0.6s ease';
        });

        // Initialisation
        window.addEventListener('load', function() {
            // Charger les données sauvegardées
            loadSavedData();
            
            // Lancer l'animation initiale
            animateOnScroll();
            
            // Démarrer l'animation après un délai
            setTimeout(animateOnScroll, 100);
            
            // Activer les événements de scroll
            window.addEventListener('scroll', animateOnScroll);
        });
    </script>
</body>
</html>
