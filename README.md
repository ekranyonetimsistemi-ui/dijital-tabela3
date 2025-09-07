<!DOCTYPE html>
<html lang="tr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>📺 Dijital Tabela Yönetim Sistemi</title>
    <style>
        * { margin: 0; padding: 0; box-sizing: border-box; }
        
        :root {
            /* Soft Color Palette */
            --primary-gradient: linear-gradient(135deg, #a8e6cf 0%, #88d8c0 100%);
            --secondary-gradient: linear-gradient(135deg, #ffd3a5 0%, #fd9853 100%);
            --accent-gradient: linear-gradient(135deg, #a8ceff 0%, #7ec8e3 100%);
            --danger-gradient: linear-gradient(135deg, #ffb3ba 0%, #ff7979 100%);
            --success-gradient: linear-gradient(135deg, #c7ffed 0%, #74c0fc 100%);
            
            --bg-primary: #f8fafc;
            --bg-secondary: #ffffff;
            --bg-soft: #f1f5f9;
            
            --text-primary: #334155;
            --text-secondary: #64748b;
            --text-muted: #94a3b8;
            
            --border-color: #e2e8f0;
            --border-soft: #f1f5f9;
            
            --shadow-soft: 0 4px 6px -1px rgba(0, 0, 0, 0.05), 0 2px 4px -1px rgba(0, 0, 0, 0.03);
            --shadow-medium: 0 10px 15px -3px rgba(0, 0, 0, 0.08), 0 4px 6px -2px rgba(0, 0, 0, 0.05);
            --shadow-large: 0 20px 25px -5px rgba(0, 0, 0, 0.1), 0 10px 10px -5px rgba(0, 0, 0, 0.04);
            
            --radius-sm: 8px;
            --radius-md: 12px;
            --radius-lg: 16px;
            --radius-xl: 20px;
        }
        
        body {
            font-family: 'Inter', 'Segoe UI', system-ui, sans-serif;
            background: var(--bg-primary);
            color: var(--text-primary);
            line-height: 1.6;
        }
        
        /* Login Screen */
        .login-screen {
            min-height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            background: linear-gradient(135deg, #667eea20 0%, #764ba220 100%);
            padding: 2rem;
        }
        
        .login-container {
            background: var(--bg-secondary);
            border-radius: var(--radius-xl);
            box-shadow: var(--shadow-large);
            padding: 3rem;
            width: 100%;
            max-width: 420px;
            text-align: center;
        }
        
        .login-logo {
            font-size: 4rem;
            margin-bottom: 1.5rem;
            filter: drop-shadow(0 4px 8px rgba(0,0,0,0.1));
        }
        
        .login-title {
            font-size: 1.875rem;
            font-weight: 600;
            margin-bottom: 0.5rem;
            color: var(--text-primary);
        }
        
        .login-subtitle {
            color: var(--text-secondary);
            margin-bottom: 2rem;
        }
        
        /* Main Dashboard */
        .main-dashboard {
            display: none;
            min-height: 100vh;
        }
        
        .dashboard-header {
            background: var(--bg-secondary);
            border-bottom: 1px solid var(--border-color);
            padding: 1.5rem 2rem;
            box-shadow: var(--shadow-soft);
        }
        
        .header-content {
            max-width: 1400px;
            margin: 0 auto;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .header-left {
            display: flex;
            align-items: center;
            gap: 1rem;
        }
        
        .header-logo {
            font-size: 2rem;
        }
        
        .header-title {
            font-size: 1.5rem;
            font-weight: 600;
            color: var(--text-primary);
        }
        
        .header-subtitle {
            font-size: 0.875rem;
            color: var(--text-secondary);
        }
        
        .header-actions {
            display: flex;
            gap: 0.75rem;
            align-items: center;
        }
        
        .user-info {
            text-align: right;
            margin-right: 1rem;
        }
        
        .user-name {
            font-weight: 500;
            font-size: 0.875rem;
            color: var(--text-primary);
        }
        
        .user-role {
            font-size: 0.75rem;
            color: var(--text-secondary);
        }
        
        /* Dashboard Content */
        .dashboard-content {
            max-width: 1400px;
            margin: 0 auto;
            padding: 2rem;
        }
        
        /* Stats Cards */
        .stats-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 1.5rem;
            margin-bottom: 2rem;
        }
        
        .stat-card {
            background: var(--bg-secondary);
            border-radius: var(--radius-lg);
            padding: 1.5rem;
            box-shadow: var(--shadow-soft);
            border: 1px solid var(--border-color);
            transition: all 0.3s ease;
        }
        
        .stat-card:hover {
            transform: translateY(-2px);
            box-shadow: var(--shadow-medium);
        }
        
        .stat-card.primary { border-left: 4px solid #a8e6cf; }
        .stat-card.secondary { border-left: 4px solid #ffd3a5; }
        .stat-card.accent { border-left: 4px solid #a8ceff; }
        .stat-card.success { border-left: 4px solid #c7ffed; }
        
        .stat-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 1rem;
        }
        
        .stat-icon {
            font-size: 1.5rem;
            opacity: 0.8;
        }
        
        .stat-number {
            font-size: 2rem;
            font-weight: 700;
            color: var(--text-primary);
        }
        
        .stat-label {
            color: var(--text-secondary);
            font-size: 0.875rem;
        }
        
        /* Quick Actions */
        .quick-actions {
            background: var(--bg-secondary);
            border-radius: var(--radius-lg);
            padding: 1.5rem;
            box-shadow: var(--shadow-soft);
            border: 1px solid var(--border-color);
            margin-bottom: 2rem;
        }
        
        .section-title {
            font-size: 1.25rem;
            font-weight: 600;
            margin-bottom: 1.5rem;
            color: var(--text-primary);
            display: flex;
            align-items: center;
            gap: 0.5rem;
        }
        
        .actions-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 1rem;
        }
        
        .action-card {
            background: var(--bg-soft);
            border: 2px solid var(--border-color);
            border-radius: var(--radius-md);
            padding: 1.5rem;
            cursor: pointer;
            transition: all 0.3s ease;
            text-align: center;
        }
        
        .action-card:hover {
            border-color: #a8e6cf;
            transform: translateY(-2px);
            box-shadow: var(--shadow-medium);
        }
        
        .action-icon {
            font-size: 2rem;
            margin-bottom: 1rem;
            opacity: 0.8;
        }
        
        .action-title {
            font-weight: 600;
            margin-bottom: 0.5rem;
            color: var(--text-primary);
        }
        
        .action-description {
            font-size: 0.875rem;
            color: var(--text-secondary);
        }
        
        /* Screens Grid */
        .screens-section {
            background: var(--bg-secondary);
            border-radius: var(--radius-lg);
            padding: 1.5rem;
            box-shadow: var(--shadow-soft);
            border: 1px solid var(--border-color);
        }
        
        .screens-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(320px, 1fr));
            gap: 1.5rem;
            margin-top: 1.5rem;
        }
        
        .screen-card {
            background: var(--bg-soft);
            border-radius: var(--radius-md);
            padding: 1.5rem;
            border: 1px solid var(--border-color);
            transition: all 0.3s ease;
            cursor: pointer;
        }
        
        .screen-card:hover {
            transform: translateY(-2px);
            box-shadow: var(--shadow-medium);
        }
        
        .screen-card.online { border-left: 4px solid #a8e6cf; }
        .screen-card.offline { border-left: 4px solid #ffb3ba; }
        
        .screen-header {
            display: flex;
            justify-content: space-between;
            align-items: flex-start;
            margin-bottom: 1rem;
        }
        
        .screen-name {
            font-weight: 600;
            color: var(--text-primary);
        }
        
        .screen-location {
            font-size: 0.875rem;
            color: var(--text-secondary);
        }
        
        .screen-status {
            padding: 0.25rem 0.75rem;
            border-radius: 1rem;
            font-size: 0.75rem;
            font-weight: 500;
        }
        
        .status-online {
            background: #c7ffed;
            color: #065f46;
        }
        
        .status-offline {
            background: #ffb3ba;
            color: #7f1d1d;
        }
        
        .screen-actions {
            display: flex;
            gap: 0.5rem;
            margin-top: 1rem;
            flex-wrap: wrap;
        }
        
        /* Buttons */
        .btn {
            padding: 0.75rem 1.5rem;
            border: none;
            border-radius: var(--radius-md);
            font-weight: 500;
            cursor: pointer;
            transition: all 0.3s ease;
            text-decoration: none;
            display: inline-flex;
            align-items: center;
            gap: 0.5rem;
            font-size: 0.875rem;
        }
        
        .btn:hover {
            transform: translateY(-1px);
        }
        
        .btn-primary { 
            background: var(--primary-gradient);
            color: white;
            box-shadow: 0 4px 14px 0 rgba(168, 230, 207, 0.39);
        }
        
        .btn-secondary { 
            background: var(--secondary-gradient);
            color: white;
            box-shadow: 0 4px 14px 0 rgba(255, 211, 165, 0.39);
        }
        
        .btn-accent { 
            background: var(--accent-gradient);
            color: white;
            box-shadow: 0 4px 14px 0 rgba(168, 206, 255, 0.39);
        }
        
        .btn-danger { 
            background: var(--danger-gradient);
            color: white;
            box-shadow: 0 4px 14px 0 rgba(255, 179, 186, 0.39);
        }
        
        .btn-success { 
            background: var(--success-gradient);
            color: white;
            box-shadow: 0 4px 14px 0 rgba(199, 255, 237, 0.39);
        }
        
        .btn-small {
            padding: 0.5rem 1rem;
            font-size: 0.75rem;
        }
        
        /* Form Elements */
        .form-group {
            margin-bottom: 1.5rem;
        }
        
        .form-label {
            display: block;
            margin-bottom: 0.5rem;
            font-weight: 500;
            color: var(--text-primary);
        }
        
        .form-input,
        .form-select,
        .form-textarea {
            width: 100%;
            padding: 0.75rem;
            border: 2px solid var(--border-color);
            border-radius: var(--radius-md);
            background: var(--bg-secondary);
            color: var(--text-primary);
            transition: all 0.3s ease;
        }
        
        .form-input:focus,
        .form-select:focus,
        .form-textarea:focus {
            outline: none;
            border-color: #a8e6cf;
            box-shadow: 0 0 0 3px rgba(168, 230, 207, 0.1);
        }
        
        /* Modals/Popups */
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.5);
            z-index: 1000;
            backdrop-filter: blur(4px);
        }
        
        .modal.active {
            display: flex;
            align-items: center;
            justify-content: center;
            padding: 1rem;
        }
        
        .modal-content {
            background: var(--bg-secondary);
            border-radius: var(--radius-xl);
            box-shadow: var(--shadow-large);
            width: 100%;
            max-width: 600px;
            max-height: 90vh;
            overflow-y: auto;
            position: relative;
        }
        
        .modal-header {
            padding: 1.5rem 2rem 1rem;
            border-bottom: 1px solid var(--border-color);
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .modal-title {
            font-size: 1.25rem;
            font-weight: 600;
            color: var(--text-primary);
        }
        
        .modal-close {
            background: none;
            border: none;
            font-size: 1.5rem;
            cursor: pointer;
            color: var(--text-muted);
            padding: 0.25rem;
            border-radius: var(--radius-sm);
            transition: all 0.3s ease;
        }
        
        .modal-close:hover {
            color: var(--text-primary);
            background: var(--bg-soft);
        }
        
        .modal-body {
            padding: 2rem;
        }
        
        .modal-footer {
            padding: 1rem 2rem 2rem;
            display: flex;
            justify-content: flex-end;
            gap: 1rem;
        }
        
        /* Tabs */
        .tab-nav {
            display: flex;
            border-bottom: 1px solid var(--border-color);
            margin-bottom: 2rem;
        }
        
        .tab-btn {
            padding: 1rem 1.5rem;
            background: none;
            border: none;
            cursor: pointer;
            color: var(--text-secondary);
            font-weight: 500;
            transition: all 0.3s ease;
            border-bottom: 2px solid transparent;
        }
        
        .tab-btn.active {
            color: var(--text-primary);
            border-bottom-color: #a8e6cf;
        }
        
        .tab-content {
            display: none;
        }
        
        .tab-content.active {
            display: block;
        }
        
        /* Content List */
        .content-list {
            max-height: 300px;
            overflow-y: auto;
            border: 1px solid var(--border-color);
            border-radius: var(--radius-md);
            padding: 1rem;
        }
        
        .content-item {
            display: flex;
            align-items: center;
            padding: 0.75rem;
            border-radius: var(--radius-sm);
            cursor: pointer;
            transition: all 0.3s ease;
            margin-bottom: 0.5rem;
            border: 2px solid transparent;
        }
        
        .content-item:hover {
            background: var(--bg-soft);
        }
        
        .content-item.selected {
            background: rgba(168, 230, 207, 0.1);
            border-color: #a8e6cf;
        }
        
        .content-icon {
            font-size: 1.5rem;
            margin-right: 1rem;
        }
        
        .content-info {
            flex: 1;
        }
        
        .content-name {
            font-weight: 500;
            color: var(--text-primary);
        }
        
        .content-type {
            font-size: 0.75rem;
            color: var(--text-secondary);
        }
        
        /* Groups */
        .groups-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
            gap: 1.5rem;
        }
        
        .group-card {
            background: var(--bg-soft);
            border-radius: var(--radius-md);
            padding: 1.5rem;
            border: 1px solid var(--border-color);
            transition: all 0.3s ease;
        }
        
        .group-card:hover {
            transform: translateY(-2px);
            box-shadow: var(--shadow-medium);
        }
        
        .group-header {
            display: flex;
            justify-content: space-between;
            align-items: flex-start;
            margin-bottom: 1rem;
            padding-bottom: 1rem;
            border-bottom: 1px solid var(--border-color);
        }
        
        .group-name {
            font-weight: 600;
            color: var(--text-primary);
        }
        
        .group-description {
            font-size: 0.875rem;
            color: var(--text-secondary);
            margin-top: 0.25rem;
        }
        
        .group-stats {
            text-align: right;
            font-size: 0.75rem;
            color: var(--text-secondary);
        }
        
        /* Notifications */
        .notification {
            position: fixed;
            top: 1rem;
            right: 1rem;
            padding: 1rem 1.5rem;
            border-radius: var(--radius-md);
            color: white;
            font-weight: 500;
            display: none;
            z-index: 2000;
            box-shadow: var(--shadow-medium);
            max-width: 400px;
        }
        
        .notification.success { background: var(--primary-gradient); }
        .notification.error { background: var(--danger-gradient); }
        .notification.info { background: var(--accent-gradient); }
        
        /* Empty State */
        .empty-state {
            text-align: center;
            padding: 3rem 1rem;
            color: var(--text-secondary);
        }
        
        .empty-icon {
            font-size: 3rem;
            margin-bottom: 1rem;
            opacity: 0.6;
        }
        
        .empty-title {
            font-size: 1.125rem;
            font-weight: 600;
            margin-bottom: 0.5rem;
            color: var(--text-primary);
        }
        
        .empty-description {
            margin-bottom: 1.5rem;
        }
        
        /* Responsive */
        @media (max-width: 768px) {
            .dashboard-content {
                padding: 1rem;
            }
            
            .stats-grid {
                grid-template-columns: 1fr;
            }
            
            .actions-grid {
                grid-template-columns: 1fr;
            }
            
            .header-content {
                flex-direction: column;
                gap: 1rem;
                text-align: center;
            }
            
            .modal-content {
                margin: 1rem;
            }
            
            .screen-actions {
                flex-direction: column;
            }
        }
        
        /* Animations */
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        @keyframes slideIn {
            from { transform: translateX(-20px); opacity: 0; }
            to { transform: translateX(0); opacity: 1; }
        }
        
        .fade-in {
            animation: fadeIn 0.5s ease-out;
        }
        
        .slide-in {
            animation: slideIn 0.5s ease-out;
        }
        
        /* Loading */
        .loading {
            display: inline-flex;
            align-items: center;
            gap: 0.5rem;
        }
        
        .loading::after {
            content: '';
            width: 1rem;
            height: 1rem;
            border: 2px solid transparent;
            border-top: 2px solid currentColor;
            border-radius: 50%;
            animation: spin 1s linear infinite;
        }
        
        @keyframes spin {
            to { transform: rotate(360deg); }
        }
    </style>
</head>
<body>
    <!-- Login Screen -->
    <div id="loginScreen" class="login-screen">
        <div class="login-container fade-in">
            <div class="login-logo">📺</div>
            <h1 class="login-title">Dijital Tabela</h1>
            <p class="login-subtitle">Yönetim Sistemi</p>
            
            <div id="loginError" style="display: none; background: #fef2f2; color: #dc2626; padding: 1rem; border-radius: 0.5rem; margin-bottom: 1rem;"></div>
            
            <form id="loginForm">
                <div class="form-group">
                    <label class="form-label">👤 Kullanıcı Adı</label>
                    <input type="text" class="form-input" id="username" required placeholder="admin">
                </div>
                
                <div class="form-group">
                    <label class="form-label">🔒 Şifre</label>
                    <input type="password" class="form-input" id="password" required placeholder="admin123">
                </div>
                
                <button type="submit" class="btn btn-primary" style="width: 100%;">
                    <span id="loginText">🚀 Giriş Yap</span>
                </button>
            </form>
            
            <div style="margin-top: 2rem; padding: 1rem; background: var(--bg-soft); border-radius: var(--radius-md); font-size: 0.875rem; color: var(--text-secondary);">
                <strong>Demo Hesap:</strong> admin / admin123
            </div>
        </div>
    </div>

    <!-- Main Dashboard -->
    <div id="mainDashboard" class="main-dashboard">
        <!-- Header -->
        <div class="dashboard-header">
            <div class="header-content">
                <div class="header-left">
                    <div class="header-logo">📊</div>
                    <div>
                        <div class="header-title">Dijital Tabela Dashboard</div>
                        <div class="header-subtitle">Merkezi Yönetim Sistemi</div>
                    </div>
                </div>
                
                <div class="header-actions">
                    <div class="user-info">
                        <div class="user-name" id="currentUser">Admin</div>
                        <div class="user-role">Sistem Yöneticisi</div>
                    </div>
                    <button class="btn btn-danger" onclick="logout()">🚪 Çıkış</button>
                </div>
            </div>
        </div>

        <!-- Dashboard Content -->
        <div class="dashboard-content">
            <!-- Stats -->
            <div class="stats-grid">
                <div class="stat-card primary">
                    <div class="stat-header">
                        <div class="stat-icon">🖥️</div>
                        <div class="stat-number" id="totalScreens">0</div>
                    </div>
                    <div class="stat-label">Toplam Ekran</div>
                </div>
                
                <div class="stat-card secondary">
                    <div class="stat-header">
                        <div class="stat-icon">🟢</div>
                        <div class="stat-number" id="onlineScreens">0</div>
                    </div>
                    <div class="stat-label">Aktif Ekran</div>
                </div>
                
                <div class="stat-card accent">
                    <div class="stat-header">
                        <div class="stat-icon">👥</div>
                        <div class="stat-number" id="totalGroups">0</div>
                    </div>
                    <div class="stat-label">Grup Sayısı</div>
                </div>
                
                <div class="stat-card success">
                    <div class="stat-header">
                        <div class="stat-icon">📁</div>
                        <div class="stat-number" id="totalContent">0</div>
                    </div>
                    <div class="stat-label">İçerik Sayısı</div>
                </div>
            </div>

            <!-- Quick Actions -->
            <div class="quick-actions">
                <div class="section-title">
                    <span>⚡</span>
                    <span>Hızlı İşlemler</span>
                </div>
                
                <div class="actions-grid">
                    <div class="action-card" onclick="openTestDisplay()">
                        <div class="action-icon">🧪</div>
                        <div class="action-title">Test Ekranı Aç</div>
                        <div class="action-description">Yeni test ekranı açarak sistemi deneyin</div>
                    </div>
                    
                    <div class="action-card" onclick="openScreenManagement()">
                        <div class="action-icon">🖥️</div>
                        <div class="action-title">Ekran Yönetimi</div>
                        <div class="action-description">Ekranları görüntüleyin ve yönetin</div>
                    </div>
                    
                    <div class="action-card" onclick="openContentManagement()">
                        <div class="action-icon">📤</div>
                        <div class="action-title">İçerik Yönetimi</div>
                        <div class="action-description">Fotoğraf ve video yükleyin</div>
                    </div>
                    
                    <div class="action-card" onclick="openGroupManagement()">
                        <div class="action-icon">👥</div>
                        <div class="action-title">Grup Yönetimi</div>
                        <div class="action-description">Ekranları gruplara ayırın</div>
                    </div>
                    
                    <div class="action-card" onclick="openContentAssignment()">
                        <div class="action-icon">🎯</div>
                        <div class="action-title">İçerik Atama</div>
                        <div class="action-description">İçerikleri ekranlara atayın</div>
                    </div>
                    
                    <div class="action-card" onclick="downloadSystemReport()">
                        <div class="action-icon">📊</div>
                        <div class="action-title">Sistem Raporu</div>
                        <div class="action-description">Detaylı sistem raporunu indirin</div>
                    </div>
                </div>
            </div>

            <!-- Recent Screens -->
            <div class="screens-section">
                <div class="section-title">
                    <span>🖥️</span>
                    <span>Son Ekranlar</span>
                </div>
                
                <div class="screens-grid" id="screensGrid">
                    <!-- Ekranlar buraya yüklenecek -->
                </div>
            </div>
        </div>
    </div>

    <!-- Screen Management Modal -->
    <div id="screenManagementModal" class="modal">
        <div class="modal-content">
            <div class="modal-header">
                <h3 class="modal-title">🖥️ Ekran Yönetimi</h3>
                <button class="modal-close" onclick="closeModal('screenManagementModal')">&times;</button>
            </div>
            <div class="modal-body">
                <div style="display: flex; justify-content: space-between; align-items: center; margin-bottom: 1.5rem;">
                    <h4>Tüm Ekranlar</h4>
                    <button class="btn btn-primary" onclick="openAddScreenModal()">➕ Yeni Ekran</button>
                </div>
                <div id="allScreensGrid" class="screens-grid">
                    <!-- Tüm ekranlar buraya -->
                </div>
            </div>
        </div>
    </div>

    <!-- Add Screen Modal -->
    <div id="addScreenModal" class="modal">
        <div class="modal-content">
            <div class="modal-header">
                <h3 class="modal-title">➕ Yeni Ekran Ekle</h3>
                <button class="modal-close" onclick="closeModal('addScreenModal')">&times;</button>
            </div>
            <div class="modal-body">
                <form id="addScreenForm">
                    <div class="form-group">
                        <label class="form-label">Ekran Adı</label>
                        <input type="text" class="form-input" id="screenName" required placeholder="Örn: Mağaza Giriş Ekranı">
                    </div>
                    <div class="form-group">
                        <label class="form-label">Konum</label>
                        <input type="text" class="form-input" id="screenLocation" required placeholder="Örn: İstanbul - Kadıköy">
                    </div>
                    <div class="form-group">
                        <label class="form-label">Grup</label>
                        <select class="form-select" id="screenGroup">
                            <option value="">Grup Seçin</option>
                        </select>
                    </div>
                    <div class="form-group">
                        <label class="form-label">Açıklama</label>
                        <textarea class="form-textarea" id="screenDescription" rows="3" placeholder="Ekran hakkında notlar..."></textarea>
                    </div>
                </form>
            </div>
            <div class="modal-footer">
                <button class="btn btn-secondary" onclick="closeModal('addScreenModal')">İptal</button>
                <button class="btn btn-primary" onclick="addScreen()">✅ Ekran Ekle</button>
            </div>
        </div>
    </div>

    <!-- Group Management Modal -->
    <div id="groupManagementModal" class="modal">
        <div class="modal-content">
            <div class="modal-header">
                <h3 class="modal-title">👥 Grup Yönetimi</h3>
                <button class="modal-close" onclick="closeModal('groupManagementModal')">&times;</button>
            </div>
            <div class="modal-body">
                <div style="display: flex; justify-content: space-between; align-items: center; margin-bottom: 1.5rem;">
                    <h4>Tüm Gruplar</h4>
                    <button class="btn btn-primary" onclick="openAddGroupModal()">➕ Yeni Grup</button>
                </div>
                <div id="allGroupsGrid" class="groups-grid">
                    <!-- Tüm gruplar buraya -->
                </div>
            </div>
        </div>
    </div>

    <!-- Add Group Modal -->
    <div id="addGroupModal" class="modal">
        <div class="modal-content">
            <div class="modal-header">
                <h3 class="modal-title">➕ Yeni Grup Oluştur</h3>
                <button class="modal-close" onclick="closeModal('addGroupModal')">&times;</button>
            </div>
            <div class="modal-body">
                <form id="addGroupForm">
                    <div class="form-group">
                        <label class="form-label">Grup Adı</label>
                        <input type="text" class="form-input" id="groupName" required placeholder="Örn: İstanbul Mağazaları">
                    </div>
                    <div class="form-group">
                        <label class="form-label">Grup Rengi</label>
                        <input type="color" class="form-input" id="groupColor" value="#a8e6cf">
                    </div>
                    <div class="form-group">
                        <label class="form-label">Açıklama</label>
                        <textarea class="form-textarea" id="groupDescription" rows="3" placeholder="Grup hakkında açıklama..."></textarea>
                    </div>
                </form>
            </div>
            <div class="modal-footer">
                <button class="btn btn-secondary" onclick="closeModal('addGroupModal')">İptal</button>
                <button class="btn btn-primary" onclick="addGroup()">✅ Grup Oluştur</button>
            </div>
        </div>
    </div>

    <!-- Content Management Modal -->
    <div id="contentManagementModal" class="modal">
        <div class="modal-content">
            <div class="modal-header">
                <h3 class="modal-title">📁 İçerik Yönetimi</h3>
                <button class="modal-close" onclick="closeModal('contentManagementModal')">&times;</button>
            </div>
            <div class="modal-body">
                <div style="border: 2px dashed #a8e6cf; border-radius: var(--radius-md); padding: 2rem; text-align: center; margin-bottom: 1.5rem; cursor: pointer;" id="uploadArea">
                    <div style="font-size: 2rem; margin-bottom: 1rem;">📤</div>
                    <h4>Dosyaları Buraya Sürükleyin</h4>
                    <p style="color: var(--text-secondary); margin: 0.5rem 0;">veya tıklayarak seçin</p>
                    <button class="btn btn-primary" onclick="document.getElementById('fileInput').click()">📁 Dosya Seç</button>
                    <p style="font-size: 0.875rem; color: var(--text-muted); margin-top: 1rem;">
                        JPG, PNG, GIF, MP4, MOV (Max: 10MB)
                    </p>
                </div>
                
                <input type="file" id="fileInput" multiple accept=".jpg,.jpeg,.png,.gif,.mp4,.mov" style="display: none;">
                
                <div id="contentGrid" class="content-list">
                    <!-- İçerikler buraya -->
                </div>
            </div>
        </div>
    </div>

    <!-- Content Assignment Modal -->
    <div id="contentAssignmentModal" class="modal">
        <div class="modal-content">
            <div class="modal-header">
                <h3 class="modal-title">🎯 İçerik Atama</h3>
                <button class="modal-close" onclick="closeModal('contentAssignmentModal')">&times;</button>
            </div>
            <div class="modal-body">
                <div style="display: grid; grid-template-columns: 1fr 1fr; gap: 2rem;">
                    <div>
                        <h4 style="margin-bottom: 1rem;">📋 Mevcut İçerikler</h4>
                        <div id="assignmentContentList" class="content-list">
                            <!-- İçerikler buraya -->
                        </div>
                    </div>
                    <div>
                        <h4 style="margin-bottom: 1rem;">🎯 Atama Hedefi</h4>
                        <div class="form-group">
                            <label class="form-label">Atama Türü</label>
                            <select class="form-select" id="assignmentType">
                                <option value="screen">Tek Ekran</option>
                                <option value="group">Grup</option>
                            </select>
                        </div>
                        <div class="form-group">
                            <label class="form-label">Hedef Seç</label>
                            <select class="form-select" id="assignmentTarget">
                                <!-- Hedefler buraya -->
                            </select>
                        </div>
                        <button class="btn btn-success" onclick="assignContent()">✅ İçerik Ata</button>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <!-- Screen Control Modal -->
    <div id="screenControlModal" class="modal">
        <div class="modal-content" style="max-width: 1000px;">
            <div class="modal-header">
                <h3 class="modal-title" id="controlModalTitle">🎮 Ekran Kontrolü</h3>
                <button class="modal-close" onclick="closeModal('screenControlModal')">&times;</button>
            </div>
            <div class="modal-body">
                <div style="display: grid; grid-template-columns: 2fr 1fr; gap: 2rem;">
                    <div>
                        <!-- Canlı Önizleme -->
                        <div style="background: #000; border-radius: var(--radius-md); height: 300px; display: flex; align-items: center; justify-content: center; margin-bottom: 1rem; position: relative; overflow: hidden;">
                            <div id="previewContent" style="color: white; text-align: center;">
                                <div style="font-size: 2rem; margin-bottom: 1rem;">📺</div>
                                <div>Önizleme yükleniyor...</div>
                            </div>
                            <div style="position: absolute; top: 10px; left: 10px; background: rgba(0,0,0,0.7); color: white; padding: 0.5rem; border-radius: 0.25rem; font-size: 0.75rem;" id="previewOverlay">
                                Bağlanıyor...
                            </div>
                        </div>
                        
                        <!-- Önizleme Kontrolleri -->
                        <div style="display: flex; gap: 0.5rem; justify-content: center;">
                            <button class="btn btn-small btn-secondary" onclick="prevContent()">◀️ Önceki</button>
                            <button class="btn btn-small btn-secondary" onclick="nextContent()">▶️ Sonraki</button>
                            <button class="btn btn-small btn-accent" onclick="openDisplayScreen(currentControlScreenId)">📺 Canlı Görüntüle</button>
                        </div>
                    </div>
                    
                    <div>
                        <!-- Ekran Bilgileri -->
                        <div style="background: var(--primary-gradient); color: white; padding: 1.5rem; border-radius: var(--radius-md); margin-bottom: 1rem;">
                            <h4 id="controlScreenName">Ekran Adı</h4>
                            <p id="controlScreenLocation" style="opacity: 0.9; margin: 0.5rem 0;">Konum</p>
                            <div style="display: flex; justify-content: space-between; align-items: center; margin-top: 1rem;">
                                <span id="controlScreenStatus">🔴 Çevrimdışı</span>
                                <span id="controlLastSeen" style="font-size: 0.75rem;">-</span>
                            </div>
                        </div>
                        
                        <!-- Atanmış İçerikler -->
                        <div>
                            <h4 style="margin-bottom: 1rem;">🎯 Atanmış İçerikler</h4>
                            <div id="assignedContentList" style="max-height: 200px; overflow-y: auto;">
                                <!-- Atanmış içerikler buraya -->
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <!-- Notification -->
    <div id="notification" class="notification"></div>

    <!-- Hidden file input for content upload -->
    <input type="file" id="hiddenFileInput" multiple accept=".jpg,.jpeg,.png,.gif,.mp4,.mov" style="display: none;">

    <script>
        // Global Variables
        let currentUser = null;
        let screens = [];
        let groups = [];
        let uploadedFiles = [];
        let assignments = {};
        let selectedContentIndex = null;
        let currentControlScreenId = null;
        let previewInterval = null;
        let previewIndex = 0;

        // System Initialization
        document.addEventListener('DOMContentLoaded', function() {
            initializeSystem();
        });

        function initializeSystem() {
            // Initialize default admin
            initializeDefaultAdmin();
            
            // Check existing session
            checkSession();
            
            // Load system data
            loadSystemData();
            
            // Setup event listeners
            setupEventListeners();
            
            console.log('🚀 Dijital Tabela Sistemi başlatıldı');
        }

        function initializeDefaultAdmin() {
            let users = JSON.parse(localStorage.getItem('admin_users') || '[]');
            
            if (users.length === 0) {
                users.push({
                    id: 1,
                    username: 'admin',
                    password: 'admin123',
                    role: 'admin',
                    created: new Date().toISOString()
                });
                localStorage.setItem('admin_users', JSON.stringify(users));
            }
        }

        function checkSession() {
            const session = localStorage.getItem('admin_session');
            if (session) {
                currentUser = JSON.parse(session);
                showDashboard();
            }
        }

        function loadSystemData() {
            screens = JSON.parse(localStorage.getItem('digital_screens') || '[]');
            groups = JSON.parse(localStorage.getItem('screen_groups') || '[]');
            uploadedFiles = JSON.parse(localStorage.getItem('uploadedFiles') || '[]');
            assignments = JSON.parse(localStorage.getItem('content_assignments') || '{}');
            
            // Create sample data if empty
            if (screens.length === 0 && groups.length === 0) {
                createSampleData();
            }
            
            updateDashboard();
        }

        function createSampleData() {
            groups = [
                {
                    id: 'group1',
                    name: 'İstanbul Mağazaları',
                    color: '#a8e6cf',
                    description: 'İstanbul bölgesindeki tüm mağazalar',
                    created: new Date().toISOString()
                },
                {
                    id: 'group2',
                    name: 'Ankara Mağazaları',
                    color: '#a8ceff',
                    description: 'Ankara bölgesindeki mağazalar',
                    created: new Date().toISOString()
                }
            ];

            screens = [
                {
                    id: 'screen1',
                    name: 'Kadıköy Mağaza - Giriş',
                    location: 'İstanbul - Kadıköy',
                    groupId: 'group1',
                    status: 'online',
                    lastSeen: new Date().toISOString(),
                    description: 'Ana giriş kapısındaki ekran',
                    created: new Date().toISOString()
                },
                {
                    id: 'screen2',
                    name: 'Kızılay Mağaza - Vitrin',
                    location: 'Ankara - Kızılay',
                    groupId: 'group2',
                    status: 'offline',
                    lastSeen: new Date(Date.now() - 1800000).toISOString(),
                    description: 'Vitrin ekranı',
                    created: new Date().toISOString()
                }
            ];

            saveSystemData();
        }

        function saveSystemData() {
            localStorage.setItem('digital_screens', JSON.stringify(screens));
            localStorage.setItem('screen_groups', JSON.stringify(groups));
            localStorage.setItem('uploadedFiles', JSON.stringify(uploadedFiles));
            localStorage.setItem('content_assignments', JSON.stringify(assignments));
        }

        // Login System
        document.getElementById('loginForm').addEventListener('submit', function(e) {
            e.preventDefault();
            
            const username = document.getElementById('username').value.trim();
            const password = document.getElementById('password').value;
            const loginBtn = e.target.querySelector('button[type="submit"]');
            const loginText = document.getElementById('loginText');
            
            if (!username || !password) {
                showLoginError('⚠️ Lütfen tüm alanları doldurun');
                return;
            }
            
            // Show loading
            loginText.innerHTML = '<span class="loading">Giriş yapılıyor</span>';
            loginBtn.disabled = true;
            
            setTimeout(() => {
                if (authenticateUser(username, password)) {
                    const sessionData = {
                        username: username,
                        role: 'admin',
                        loginTime: new Date().toISOString()
                    };
                    
                    localStorage.setItem('admin_session', JSON.stringify(sessionData));
                    currentUser = sessionData;
                    
                    showDashboard();
                    showNotification('✅ Başarıyla giriş yapıldı!', 'success');
                } else {
                    showLoginError('❌ Geçersiz kullanıcı adı veya şifre');
                    loginText.textContent = '🚀 Giriş Yap';
                    loginBtn.disabled = false;
                    document.getElementById('password').value = '';
                }
            }, 1000);
        });

        function authenticateUser(username, password) {
            const users = JSON.parse(localStorage.getItem('admin_users') || '[]');
            return users.some(user => user.username === username && user.password === password);
        }

        function showLoginError(message) {
            const errorDiv = document.getElementById('loginError');
            errorDiv.textContent = message;
            errorDiv.style.display = 'block';
            
            setTimeout(() => {
                errorDiv.style.display = 'none';
            }, 3000);
        }

        function showDashboard() {
            document.getElementById('loginScreen').style.display = 'none';
            document.getElementById('mainDashboard').style.display = 'block';
            
            if (currentUser) {
                document.getElementById('currentUser').textContent = currentUser.username;
            }
            
            updateDashboard();
        }

        function updateDashboard() {
            document.getElementById('totalScreens').textContent = screens.length;
            document.getElementById('onlineScreens').textContent = screens.filter(s => s.status === 'online').length;
            document.getElementById('totalGroups').textContent = groups.length;
            document.getElementById('totalContent').textContent = uploadedFiles.length;
            
            loadRecentScreens();
        }

        function loadRecentScreens() {
            const container = document.getElementById('screensGrid');
            
            if (screens.length === 0) {
                container.innerHTML = `
                    <div class="empty-state" style="grid-column: 1/-1;">
                        <div class="empty-icon">🖥️</div>
                        <div class="empty-title">Henüz ekran eklenmemiş</div>
                        <div class="empty-description">İlk ekranınızı ekleyerek başlayın</div>
                        <button class="btn btn-primary" onclick="openAddScreenModal()">➕ İlk Ekranı Ekle</button>
                    </div>
                `;
                return;
            }

            const recentScreens = screens.slice(-6);
            
            container.innerHTML = recentScreens.map(screen => {
                const group = groups.find(g => g.id === screen.groupId);
                const timeDiff = Date.now() - new Date(screen.lastSeen).getTime();
                const minutesAgo = Math.floor(timeDiff / 60000);
                
                return `
                    <div class="screen-card ${screen.status}" onclick="openScreenControl('${screen.id}')">
                        <div class="screen-header">
                            <div>
                                <div class="screen-name">${screen.name}</div>
                                <div class="screen-location">📍 ${screen.location}</div>
                            </div>
                            <span class="screen-status status-${screen.status}">
                                ${screen.status === 'online' ? '🟢 Aktif' : '🔴 Çevrimdışı'}
                            </span>
                        </div>
                        
                        <div style="margin: 1rem 0; font-size: 0.875rem; color: var(--text-secondary);">
                            ${group ? `👥 ${group.name}` : 'Grup Yok'}<br>
                            Son görülme: ${minutesAgo < 1 ? 'Şimdi' : minutesAgo + ' dk önce'}
                        </div>
                        
                        <div class="screen-actions" onclick="event.stopPropagation()">
                            <button class="btn btn-small btn-primary" onclick="openScreenControl('${screen.id}')">🎮 Kontrol</button>
                            <button class="btn btn-small btn-accent" onclick="openDisplayScreen('${screen.id}')">📺 Görüntüle</button>
                        </div>
                    </div>
                `;
            }).join('');
        }

        // Quick Actions
        function openTestDisplay() {
            const displayWindow = window.open('', 'test_display', 'width=1200,height=800');
            createDisplayWindow(displayWindow);
            showNotification('🧪 Test ekranı açıldı!', 'success');
        }

        function createDisplayWindow(win) {
            win.document.write(`
                <!DOCTYPE html>
                <html>
                <head>
                    <title>Dijital Tabela - Görüntüleme</title>
                    <style>
                        body { margin: 0; background: #000; color: white; font-family: Arial; display: flex; align-items: center; justify-content: center; height: 100vh; }
                        .content { text-align: center; }
                    </style>
                </head>
                <body>
                    <div class="content">
                        <h1 style="font-size: 3em;">📺</h1>
                        <h2>Dijital Tabela Test Ekranı</h2>
                        <p>Sistem başarıyla çalışıyor!</p>
                        <p style="margin-top: 2em; font-size: 0.9em; opacity: 0.7;">${new Date().toLocaleString('tr-TR')}</p>
                    </div>
                </body>
                </html>
            `);
        }

        function openScreenManagement() {
            document.getElementById('screenManagementModal').classList.add('active');
            loadAllScreens();
        }

        function openContentManagement() {
            document.getElementById('contentManagementModal').classList.add('active');
            loadContentGrid();
        }

        function openGroupManagement() {
            document.getElementById('groupManagementModal').classList.add('active');
            loadAllGroups();
        }

        function openContentAssignment() {
            document.getElementById('contentAssignmentModal').classList.add('active');
            loadAssignmentContent();
            updateAssignmentTargets();
        }

        function downloadSystemReport() {
            const report = {
                timestamp: new Date().toISOString(),
                totalScreens: screens.length,
                onlineScreens: screens.filter(s => s.status === 'online').length,
                totalGroups: groups.length,
                totalContent: uploadedFiles.length,
                screens: screens,
                groups: groups,
                assignments: assignments
            };
            
            const dataStr = JSON.stringify(report, null, 2);
            const blob = new Blob([dataStr], {type: 'application/json'});
            const url = URL.createObjectURL(blob);
            
            const link = document.createElement('a');
            link.href = url;
            link.download = `dijital-tabela-rapor-${new Date().toISOString().split('T')[0]}.json`;
            link.click();
            
            URL.revokeObjectURL(url);
            showNotification('📊 Sistem raporu indirildi!', 'success');
        }

        // Modal Management
        function closeModal(modalId) {
            document.getElementById(modalId).classList.remove('active');
        }

        function openAddScreenModal() {
            // Load group options
            const groupSelect = document.getElementById('screenGroup');
            groupSelect.innerHTML = '<option value="">Grup Seçin</option>';
            groups.forEach(group => {
                const option = document.createElement('option');
                option.value = group.id;
                option.textContent = group.name;
                groupSelect.appendChild(option);
            });
            
            document.getElementById('addScreenModal').classList.add('active');
        }

        function openAddGroupModal() {
            document.getElementById('addGroupModal').classList.add('active');
        }

        function addScreen() {
            const name = document.getElementById('screenName').value.trim();
            const location = document.getElementById('screenLocation').value.trim();
            const groupId = document.getElementById('screenGroup').value;
            const description = document.getElementById('screenDescription').value.trim();
            
            if (!name || !location) {
                showNotification('⚠️ Lütfen zorunlu alanları doldurun', 'error');
                return;
            }
            
            const newScreen = {
                id: 'screen_' + Date.now(),
                name: name,
                location: location,
                groupId: groupId || null,
                status: 'offline',
                lastSeen: new Date().toISOString(),
                description: description,
                created: new Date().toISOString()
            };
            
            screens.push(newScreen);
            saveSystemData();
            
            closeModal('addScreenModal');
            document.getElementById('addScreenForm').reset();
            
            updateDashboard();
            loadAllScreens();
            
            showNotification('✅ Ekran başarıyla eklendi!', 'success');
        }

        function addGroup() {
            const name = document.getElementById('groupName').value.trim();
            const color = document.getElementById('groupColor').value;
            const description = document.getElementById('groupDescription').value.trim();
            
            if (!name) {
                showNotification('⚠️ Lütfen grup adını girin', 'error');
                return;
            }
            
            const newGroup = {
                id: 'group_' + Date.now(),
                name: name,
                color: color,
                description: description,
                created: new Date().toISOString()
            };
            
            groups.push(newGroup);
            saveSystemData();
            
            closeModal('addGroupModal');
            document.getElementById('addGroupForm').reset();
            
            updateDashboard();
            loadAllGroups();
            
            showNotification('✅ Grup başarıyla oluşturuldu!', 'success');
        }

        function loadAllScreens() {
            const container = document.getElementById('allScreensGrid');
            
            if (screens.length === 0) {
                container.innerHTML = `
                    <div class="empty-state" style="grid-column: 1/-1;">
                        <div class="empty-icon">🖥️</div>
                        <div class="empty-title">Henüz ekran eklenmemiş</div>
                        <button class="btn btn-primary" onclick="openAddScreenModal()">➕ İlk Ekranı Ekle</button>
                    </div>
                `;
                return;
            }
            
            container.innerHTML = screens.map(screen => {
                const group = groups.find(g => g.id === screen.groupId);
                const timeDiff = Date.now() - new Date(screen.lastSeen).getTime();
                const minutesAgo = Math.floor(timeDiff / 60000);
                
                return `
                    <div class="screen-card ${screen.status}">
                        <div class="screen-header">
                            <div>
                                <div class="screen-name">${screen.name}</div>
                                <div class="screen-location">📍 ${screen.location}</div>
                            </div>
                            <span class="screen-status status-${screen.status}">
                                ${screen.status === 'online' ? '🟢 Aktif' : '🔴 Çevrimdışı'}
                            </span>
                        </div>
                        
                        <div style="margin: 1rem 0; font-size: 0.875rem; color: var(--text-secondary);">
                            ${group ? `👥 ${group.name}` : 'Grup Yok'}<br>
                            Son görülme: ${minutesAgo < 1 ? 'Şimdi' : minutesAgo + ' dk önce'}
                        </div>
                        
                        <div class="screen-actions">
                            <button class="btn btn-small btn-primary" onclick="openScreenControl('${screen.id}')">🎮 Kontrol</button>
                            <button class="btn btn-small btn-accent" onclick="openDisplayScreen('${screen.id}')">📺 Görüntüle</button>
                            <button class="btn btn-small btn-danger" onclick="deleteScreen('${screen.id}')">🗑️ Sil</button>
                        </div>
                    </div>
                `;
            }).join('');
        }

        function loadAllGroups() {
            const container = document.getElementById('allGroupsGrid');
            
            if (groups.length === 0) {
                container.innerHTML = `
                    <div class="empty-state" style="grid-column: 1/-1;">
                        <div class="empty-icon">👥</div>
                        <div class="empty-title">Henüz grup oluşturulmamış</div>
                        <button class="btn btn-primary" onclick="openAddGroupModal()">➕ İlk Grubu Oluştur</button>
                    </div>
                `;
                return;
            }
            
            container.innerHTML = groups.map(group => {
                const groupScreens = screens.filter(s => s.groupId === group.id);
                const onlineCount = groupScreens.filter(s => s.status === 'online').length;
                
                return `
                    <div class="group-card">
                        <div class="group-header">
                            <div>
                                <div class="group-name" style="color: ${group.color};">${group.name}</div>
                                <div class="group-description">${group.description}</div>
                            </div>
                            <div class="group-stats">
                                <div>${groupScreens.length} ekran</div>
                                <div>${onlineCount} aktif</div>
                            </div>
                        </div>
                        
                        <div style="max-height: 150px; overflow-y: auto; margin-bottom: 1rem;">
                            ${groupScreens.length > 0 ? groupScreens.map(screen => `
                                <div style="display: flex; justify-content: space-between; align-items: center; padding: 0.5rem 0; border-bottom: 1px solid var(--border-color);">
                                    <div>
                                        <div style="font-weight: 500; font-size: 0.875rem;">${screen.name}</div>
                                        <div style="font-size: 0.75rem; color: var(--text-secondary);">${screen.location}</div>
                                    </div>
                                    <span class="screen-status status-${screen.status}">
                                        ${screen.status === 'online' ? '🟢' : '🔴'}
                                    </span>
                                </div>
                            `).join('') : '<div style="text-align: center; color: var(--text-secondary); font-style: italic; padding: 1rem;">Bu grupta ekran bulunmuyor</div>'}
                        </div>
                        
                        <div style="display: flex; gap: 0.5rem;">
                            <button class="btn btn-small btn-accent" onclick="openGroupDisplays('${group.id}')">📺 Tüm Ekranları Aç</button>
                            <button class="btn btn-small btn-danger" onclick="deleteGroup('${group.id}')">🗑️ Sil</button>
                        </div>
                    </div>
                `;
            }).join('');
        }

        // Content Management
        function setupEventListeners() {
            // File upload
            document.getElementById('fileInput').addEventListener('change', handleFileUpload);
            document.getElementById('hiddenFileInput').addEventListener('change', handleFileUpload);
            
            // Upload area drag & drop
            const uploadArea = document.getElementById('uploadArea');
            if (uploadArea) {
                uploadArea.addEventListener('dragover', (e) => {
                    e.preventDefault();
                    uploadArea.style.borderColor = '#a8e6cf';
                    uploadArea.style.background = 'rgba(168, 230, 207, 0.1)';
                });
                
                uploadArea.addEventListener('dragleave', () => {
                    uploadArea.style.borderColor = '#a8e6cf';
                    uploadArea.style.background = 'transparent';
                });
                
                uploadArea.addEventListener('drop', (e) => {
                    e.preventDefault();
                    uploadArea.style.borderColor = '#a8e6cf';
                    uploadArea.style.background = 'transparent';
                    handleFiles(e.dataTransfer.files);
                });
                
                uploadArea.addEventListener('click', () => {
                    document.getElementById('fileInput').click();
                });
            }
        }

        async function handleFileUpload(e) {
            const files = Array.from(e.target.files);
            await handleFiles(files);
            e.target.value = ''; // Reset input
        }

        async function handleFiles(files) {
            for (let file of files) {
                await uploadFile(file);
            }
            loadContentGrid();
        }

        async function uploadFile(file) {
            if (file.size > 10 * 1024 * 1024) {
                showNotification('⚠️ Dosya çok büyük! Maksimum 10MB', 'error');
                return;
            }
            
            const allowedTypes = ['image/jpeg', 'image/png', 'image/gif', 'video/mp4', 'video/quicktime'];
            if (!allowedTypes.includes(file.type)) {
                showNotification('⚠️ Desteklenmeyen dosya türü!', 'error');
                return;
            }
            
            try {
                const base64Data = await fileToBase64(file);
                
                const fileInfo = {
                    name: file.name,
                    type: file.type.startsWith('image/') ? 'image' : 'video',
                    size: file.size,
                    data: base64Data,
                    uploadDate: new Date().toISOString(),
                    uploadedBy: currentUser.username
                };
                
                uploadedFiles.push(fileInfo);
                saveSystemData();
                
                showNotification(`✅ ${file.name} yüklendi!`, 'success');
                updateDashboard();
                
            } catch (error) {
                showNotification('❌ Yükleme hatası!', 'error');
            }
        }

        function fileToBase64(file) {
            return new Promise((resolve, reject) => {
                const reader = new FileReader();
                reader.readAsDataURL(file);
                reader.onload = () => resolve(reader.result);
                reader.onerror = error => reject(error);
            });
        }

        function loadContentGrid() {
            const container = document.getElementById('contentGrid');
            
            if (uploadedFiles.length === 0) {
                container.innerHTML = `
                    <div class="empty-state">
                        <div class="empty-icon">📁</div>
                        <div class="empty-title">Henüz içerik yüklenmemiş</div>
                        <div class="empty-description">Fotoğraf veya video yükleyerek başlayın</div>
                    </div>
                `;
                return;
            }
            
            container.innerHTML = uploadedFiles.map((file, index) => `
                <div class="content-item">
                    <div class="content-icon">${file.type === 'image' ? '🖼️' : '🎥'}</div>
                    <div class="content-info">
                        <div class="content-name">${file.name}</div>
                        <div class="content-type">${file.type === 'image' ? 'Fotoğraf' : 'Video'} • ${(file.size / 1024 / 1024).toFixed(2)} MB</div>
                    </div>
                    <button class="btn btn-small btn-danger" onclick="deleteContent(${index})">🗑️</button>
                </div>
            `).join('');
        }

        function deleteContent(index) {
            if (confirm('Bu içeriği silmek istediğinizden emin misiniz?')) {
                uploadedFiles.splice(index, 1);
                saveSystemData();
                loadContentGrid();
                updateDashboard();
                showNotification('🗑️ İçerik silindi!', 'success');
            }
        }

        // Content Assignment
        function loadAssignmentContent() {
            const container = document.getElementById('assignmentContentList');
            
            if (uploadedFiles.length === 0) {
                container.innerHTML = `
                    <div class="empty-state">
                        <div class="empty-icon">📁</div>
                        <div class="empty-title">Henüz içerik yüklenmemiş</div>
                    </div>
                `;
                return;
            }
            
            container.innerHTML = uploadedFiles.map((file, index) => `
                <div class="content-item" onclick="selectContent(${index})" id="content-${index}">
                    <div class="content-icon">${file.type === 'image' ? '🖼️' : '🎥'}</div>
                    <div class="content-info">
                        <div class="content-name">${file.name}</div>
                        <div class="content-type">${file.type === 'image' ? 'Fotoğraf' : 'Video'}</div>
                    </div>
                </div>
            `).join('');
        }

        function updateAssignmentTargets() {
            const typeSelect = document.getElementById('assignmentType');
            const targetSelect = document.getElementById('assignmentTarget');
            
            function updateTargets() {
                const type = typeSelect.value;
                targetSelect.innerHTML = '';
                
                if (type === 'screen') {
                    screens.forEach(screen => {
                        const option = document.createElement('option');
                        option.value = screen.id;
                        option.textContent = `${screen.name} (${screen.location})`;
                        targetSelect.appendChild(option);
                    });
                } else if (type === 'group') {
                    groups.forEach(group => {
                        const option = document.createElement('option');
                        option.value = group.id;
                        option.textContent = group.name;
                        targetSelect.appendChild(option);
                    });
                }
            }
            
            typeSelect.addEventListener('change', updateTargets);
            updateTargets();
        }

        function selectContent(index) {
            // Clear previous selection
            document.querySelectorAll('[id^="content-"]').forEach(item => {
                item.classList.remove('selected');
            });
            
            // Select new content
            document.getElementById(`content-${index}`).classList.add('selected');
            selectedContentIndex = index;
        }

        function assignContent() {
            if (selectedContentIndex === null) {
                showNotification('⚠️ Lütfen bir içerik seçin!', 'error');
                return;
            }
            
            const assignmentType = document.getElementById('assignmentType').value;
            const targetId = document.getElementById('assignmentTarget').value;
            
            if (!targetId) {
                showNotification('⚠️ Lütfen bir hedef seçin!', 'error');
                return;
            }
            
            const selectedContent = uploadedFiles[selectedContentIndex];
            
            if (!assignments[targetId]) {
                assignments[targetId] = [];
            }
            
            // Check for duplicate
            const existingAssignment = assignments[targetId].find(a => a.contentIndex === selectedContentIndex);
            if (existingAssignment) {
                showNotification('⚠️ Bu içerik zaten atanmış!', 'error');
                return;
            }
            
            assignments[targetId].push({
                contentIndex: selectedContentIndex,
                contentName: selectedContent.name,
                assignedAt: new Date().toISOString(),
                type: assignmentType
            });
            
            saveSystemData();
            
            const targetName = assignmentType === 'screen' ? 
                screens.find(s => s.id === targetId)?.name : 
                groups.find(g => g.id === targetId)?.name;
            
            showNotification(`✅ İçerik atandı: ${selectedContent.name} → ${targetName}`, 'success');
            
            // Clear selection
            selectedContentIndex = null;
            document.querySelectorAll('[id^="content-"]').forEach(item => {
                item.classList.remove('selected');
            });
        }

        // Screen Control
        function openScreenControl(screenId) {
            const screen = screens.find(s => s.id === screenId);
            if (!screen) return;
            
            currentControlScreenId = screenId;
            
            // Update modal content
            document.getElementById('controlModalTitle').textContent = `🎮 ${screen.name} - Kontrol`;
            document.getElementById('controlScreenName').textContent = screen.name;
            document.getElementById('controlScreenLocation').textContent = screen.location;
            
            const timeDiff = Date.now() - new Date(screen.lastSeen).getTime();
            const minutesAgo = Math.floor(timeDiff / 60000);
            
            document.getElementById('controlScreenStatus').innerHTML = screen.status === 'online' ? 
                '🟢 Aktif' : '🔴 Çevrimdışı';
            document.getElementById('controlLastSeen').textContent = 
                minutesAgo < 1 ? 'Şimdi' : minutesAgo + ' dk önce';
            
            // Load assigned content
            loadAssignedContent(screenId);
            
            // Start preview
            startPreview(screenId);
            
            document.getElementById('screenControlModal').classList.add('active');
        }

        function loadAssignedContent(screenId) {
            const container = document.getElementById('assignedContentList');
            const screenAssignments = assignments[screenId] || [];
            
            if (screenAssignments.length === 0) {
                container.innerHTML = `
                    <div class="empty-state">
                        <div class="empty-icon">📝</div>
                        <div class="empty-title">İçerik atanmamış</div>
                    </div>
                `;
                return;
            }
            
            container.innerHTML = screenAssignments.map(assignment => {
                const file = uploadedFiles[assignment.contentIndex];
                if (!file) return '';
                
                return `
                    <div class="content-item">
                        <div class="content-icon">${file.type === 'image' ? '🖼️' : '🎥'}</div>
                        <div class="content-info">
                            <div class="content-name">${file.name}</div>
                            <div class="content-type">${file.type === 'image' ? 'Fotoğraf' : 'Video'}</div>
                        </div>
                    </div>
                `;
            }).join('');
        }

        function startPreview(screenId) {
            const screenAssignments = assignments[screenId] || [];
            
            if (screenAssignments.length === 0) {
                document.getElementById('previewContent').innerHTML = `
                    <div style="color: white; text-align: center;">
                        <div style="font-size: 2rem; margin-bottom: 1rem;">📺</div>
                        <div>İçerik atanmamış</div>
                    </div>
                `;
                document.getElementById('previewOverlay').textContent = 'İçerik Yok';
                return;
            }
            
            previewIndex = 0;
            showPreviewContent(screenId, previewIndex);
            
            // Auto-advance preview
            if (screenAssignments.length > 1) {
                if (previewInterval) clearInterval(previewInterval);
                previewInterval = setInterval(() => {
                    previewIndex = (previewIndex + 1) % screenAssignments.length;
                    showPreviewContent(screenId, previewIndex);
                }, 3000);
            }
        }

        function showPreviewContent(screenId, index) {
            const screenAssignments = assignments[screenId] || [];
            if (index >= screenAssignments.length) return;
            
            const assignment = screenAssignments[index];
            const file = uploadedFiles[assignment.contentIndex];
            
            if (!file) return;
            
            const container = document.getElementById('previewContent');
            
            if (file.type === 'image') {
                container.innerHTML = `<img src="${file.data}" alt="${file.name}" style="max-width: 100%; max-height: 100%; object-fit: contain;">`;
            } else {
                container.innerHTML = `
                    <video src="${file.data}" autoplay muted loop style="max-width: 100%; max-height: 100%; object-fit: contain;">
                        Video oynatılamıyor
                    </video>
                `;
            }
            
            document.getElementById('previewOverlay').textContent = 
                `${index + 1}/${screenAssignments.length} - ${file.name}`;
        }

        function nextContent() {
            if (!currentControlScreenId) return;
            const screenAssignments = assignments[currentControlScreenId] || [];
            if (screenAssignments.length === 0) return;
            
            previewIndex = (previewIndex + 1) % screenAssignments.length;
            showPreviewContent(currentControlScreenId, previewIndex);
        }

        function prevContent() {
            if (!currentControlScreenId) return;
            const screenAssignments = assignments[currentControlScreenId] || [];
            if (screenAssignments.length === 0) return;
            
            previewIndex = previewIndex === 0 ? screenAssignments.length - 1 : previewIndex - 1;
            showPreviewContent(currentControlScreenId, previewIndex);
        }

        function openDisplayScreen(screenId) {
            const displayWindow = window.open('', `display_${screenId}`, 'width=1280,height=720,fullscreen=yes');
            createDisplayWindow(displayWindow, screenId);
            showNotification('📺 Görüntüleme ekranı açıldı!', 'success');
        }

        function openGroupDisplays(groupId) {
            const group = groups.find(g => g.id === groupId);
            const groupScreens = screens.filter(s => s.groupId === groupId);
            
            if (groupScreens.length === 0) {
                showNotification('⚠️ Bu grupta ekran bulunmuyor!', 'error');
                return;
            }
            
            if (confirm(`${group.name} grubundaki ${groupScreens.length} ekranı açmak istediğinizden emin misiniz?`)) {
                groupScreens.forEach((screen, index) => {
                    setTimeout(() => {
                        openDisplayScreen(screen.id);
                    }, index * 500);
                });
                
                showNotification(`📺 ${group.name} - ${groupScreens.length} ekran açıldı!`, 'success');
            }
        }

        // Delete Functions
        function deleteScreen(screenId) {
            if (confirm('Bu ekranı silmek istediğinizden emin misiniz?')) {
                const screenIndex = screens.findIndex(s => s.id === screenId);
                if (screenIndex > -1) {
                    const screenName = screens[screenIndex].name;
                    screens.splice(screenIndex, 1);
                    
                    // Delete assignments
                    delete assignments[screenId];
                    
                    saveSystemData();
                    updateDashboard();
                    loadAllScreens();
                    
                    showNotification(`🗑️ ${screenName} silindi!`, 'success');
                }
            }
        }

        function deleteGroup(groupId) {
            if (confirm('Bu grubu silmek istediğinizden emin misiniz? Gruptaki ekranlar gruptan çıkarılacak.')) {
                const groupIndex = groups.findIndex(g => g.id === groupId);
                if (groupIndex > -1) {
                    const groupName = groups[groupIndex].name;
                    
                    // Remove group from screens
                    screens.forEach(screen => {
                        if (screen.groupId === groupId) {
                            screen.groupId = null;
                        }
                    });
                    
                    // Delete group assignments
                    delete assignments[groupId];
                    
                    groups.splice(groupIndex, 1);
                    saveSystemData();
                    updateDashboard();
                    loadAllGroups();
                    
                    showNotification(`🗑️ ${groupName} silindi!`, 'success');
                }
            }
        }

        // Utility Functions
        function logout() {
            if (confirm('Çıkış yapmak istediğinizden emin misiniz?')) {
                localStorage.removeItem('admin_session');
                currentUser = null;
                
                // Clear modals
                document.querySelectorAll('.modal').forEach(modal => {
                    modal.classList.remove('active');
                });
                
                // Clear intervals
                if (previewInterval) {
                    clearInterval(previewInterval);
                    previewInterval = null;
                }
                
                // Show login screen
                document.getElementById('mainDashboard').style.display = 'none';
                document.getElementById('loginScreen').style.display = 'flex';
                
                // Reset form
                document.getElementById('loginForm').reset();
                document.getElementById('loginText').textContent = '🚀 Giriş Yap';
                
                showNotification('👋 Başarıyla çıkış yapıldı!', 'success');
            }
        }

        function showNotification(message, type) {
            const notification = document.getElementById('notification');
            notification.textContent = message;
            notification.className = `notification ${type}`;
            notification.style.display = 'block';
            
            setTimeout(() => {
                notification.style.display = 'none';
            }, 3000);
        }

        // Close modals when clicking outside
        document.addEventListener('click', function(e) {
            if (e.target.classList.contains('modal')) {
                e.target.classList.remove('active');
            }
        });

        // Cleanup intervals on page unload
        window.addEventListener('beforeunload', () => {
            if (previewInterval) {
                clearInterval(previewInterval);
            }
        });

        console.log('📺 Dijital Tabela Sistemi v3.0 - Tek Sayfa Sürümü');
        console.log('🎨 Soft renkler ve modern tasarım aktif');
        console.log('🚀 Tüm özellikler popup modallerde yönetiliyor');
    </script>
</body>
</html>
