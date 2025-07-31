<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>想法分享社区</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        :root {
            --primary: #4361ee;
            --secondary: #3f37c9;
            --success: #4cc9f0;
            --danger: #f72585;
            --light: #f8f9fa;
            --dark: #212529;
            --gray: #6c757d;
            --light-gray: #e9ecef;
            --shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
            --border: 1px solid #dee2e6;
        }
        
        body {
            background-color: #f0f2f5;
            color: var(--dark);
            line-height: 1.6;
        }
        
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 15px;
        }
        
        /* 导航栏样式 */
        header {
            background-color: white;
            box-shadow: var(--shadow);
            position: sticky;
            top: 0;
            z-index: 100;
        }
        
        .navbar {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 15px 0;
        }
        
        .logo {
            display: flex;
            align-items: center;
            font-size: 24px;
            font-weight: 700;
            color: var(--primary);
            text-decoration: none;
        }
        
        .logo i {
            margin-right: 8px;
        }
        
        .nav-links {
            display: flex;
            list-style: none;
        }
        
        .nav-links li {
            margin-left: 20px;
        }
        
        .nav-links a {
            text-decoration: none;
            color: var(--dark);
            font-weight: 500;
            transition: color 0.3s;
        }
        
        .nav-links a:hover {
            color: var(--primary);
        }
        
        .user-actions {
            display: flex;
            align-items: center;
        }
        
        .btn {
            padding: 8px 16px;
            border-radius: 6px;
            font-weight: 500;
            cursor: pointer;
            transition: all 0.3s;
            border: none;
        }
        
        .btn-primary {
            background-color: var(--primary);
            color: white;
        }
        
        .btn-primary:hover {
            background-color: var(--secondary);
        }
        
        .btn-outline {
            background: transparent;
            border: 1px solid var(--primary);
            color: var(--primary);
            margin-left: 10px;
        }
        
        .btn-outline:hover {
            background-color: var(--primary);
            color: white;
        }
        
        /* 主要内容区域 */
        .main-content {
            display: grid;
            grid-template-columns: 1fr 3fr;
            gap: 20px;
            padding: 30px 0;
        }
        
        /* 侧边栏 */
        .sidebar {
            background: white;
            border-radius: 10px;
            box-shadow: var(--shadow);
            padding: 20px;
            height: fit-content;
        }
        
        .sidebar h3 {
            margin-bottom: 15px;
            padding-bottom: 10px;
            border-bottom: var(--border);
        }
        
        .trending-topics {
            list-style: none;
        }
        
        .trending-topics li {
            padding: 8px 0;
            border-bottom: var(--border);
        }
        
        .trending-topics li:last-child {
            border-bottom: none;
        }
        
        .trending-topics a {
            text-decoration: none;
            color: var(--dark);
            display: flex;
            align-items: center;
        }
        
        .trending-topics a:hover {
            color: var(--primary);
        }
        
        .trending-topics i {
            margin-right: 8px;
            color: var(--gray);
        }
        
        /* 内容区域 */
        .content-area {
            display: flex;
            flex-direction: column;
            gap: 20px;
        }
        
        /* 创建卡片 */
        .create-card {
            background: white;
            border-radius: 10px;
            box-shadow: var(--shadow);
            padding: 20px;
        }
        
        .create-card textarea {
            width: 100%;
            height: 100px;
            border: var(--border);
            border-radius: 8px;
            padding: 15px;
            resize: vertical;
            margin-bottom: 15px;
            font-size: 16px;
        }
        
        .media-upload {
            display: flex;
            gap: 15px;
            margin-bottom: 15px;
        }
        
        .upload-btn {
            display: flex;
            align-items: center;
            cursor: pointer;
            color: var(--gray);
            font-size: 14px;
        }
        
        .upload-btn i {
            margin-right: 5px;
            font-size: 18px;
        }
        
        .upload-btn:hover {
            color: var(--primary);
        }
        
        /* 帖子卡片 */
        .post-card {
            background: white;
            border-radius: 10px;
            box-shadow: var(--shadow);
            overflow: hidden;
        }
        
        .post-header {
            display: flex;
            align-items: center;
            padding: 15px 20px;
            border-bottom: var(--border);
        }
        
        .user-avatar {
            width: 40px;
            height: 40px;
            border-radius: 50%;
            background-color: var(--light-gray);
            display: flex;
            align-items: center;
            justify-content: center;
            margin-right: 12px;
            font-weight: bold;
            color: var(--primary);
        }
        
        .user-info {
            flex: 1;
        }
        
        .user-info .username {
            font-weight: 600;
            color: var(--dark);
        }
        
        .user-info .post-time {
            font-size: 12px;
            color: var(--gray);
        }
        
        .post-actions {
            position: relative;
        }
        
        .post-actions .dropdown-btn {
            background: none;
            border: none;
            cursor: pointer;
            font-size: 18px;
            color: var(--gray);
        }
        
        .dropdown-content {
            position: absolute;
            right: 0;
            top: 100%;
            background: white;
            border-radius: 6px;
            box-shadow: var(--shadow);
            min-width: 150px;
            display: none;
            z-index: 10;
        }
        
        .dropdown-content.show {
            display: block;
        }
        
        .dropdown-content button {
            width: 100%;
            text-align: left;
            padding: 10px 15px;
            background: none;
            border: none;
            cursor: pointer;
            transition: background 0.3s;
        }
        
        .dropdown-content button:hover {
            background: var(--light-gray);
        }
        
        .post-content {
            padding: 20px;
        }
        
        .post-text {
            margin-bottom: 15px;
        }
        
        .post-media {
            margin-bottom: 15px;
            border-radius: 8px;
            overflow: hidden;
        }
        
        .post-media img {
            width: 100%;
            height: auto;
            display: block;
        }
        
        .post-media video {
            width: 100%;
            max-height: 500px;
            display: block;
        }
        
        .post-stats {
            display: flex;
            padding: 10px 20px;
            border-top: var(--border);
            border-bottom: var(--border);
            color: var(--gray);
            font-size: 14px;
        }
        
        .post-stats span {
            margin-right: 20px;
            display: flex;
            align-items: center;
        }
        
        .post-stats i {
            margin-right: 5px;
        }
        
        .post-interactions {
            display: flex;
            padding: 10px 20px;
            justify-content: space-around;
            border-bottom: var(--border);
        }
        
        .interaction-btn {
            display: flex;
            align-items: center;
            background: none;
            border: none;
            color: var(--gray);
            cursor: pointer;
            font-size: 14px;
            font-weight: 500;
            transition: color 0.3s;
        }
        
        .interaction-btn i {
            margin-right: 5px;
            font-size: 18px;
        }
        
        .interaction-btn:hover {
            color: var(--primary);
        }
        
        /* 评论区域 */
        .comments-section {
            padding: 15px 20px;
        }
        
        .comment-form {
            display: flex;
            gap: 10px;
            margin-bottom: 20px;
        }
        
        .comment-form input {
            flex: 1;
            padding: 10px 15px;
            border: var(--border);
            border-radius: 20px;
            font-size: 14px;
        }
        
        .comment-form button {
            background: var(--primary);
            color: white;
            border: none;
            border-radius: 20px;
            padding: 0 20px;
            cursor: pointer;
        }
        
        .comment-list {
            display: flex;
            flex-direction: column;
            gap: 15px;
        }
        
        .comment {
            display: flex;
            gap: 10px;
        }
        
        .comment-avatar {
            width: 32px;
            height: 32px;
            border-radius: 50%;
            background-color: var(--light-gray);
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 12px;
            font-weight: bold;
            color: var(--primary);
            flex-shrink: 0;
        }
        
        .comment-content {
            flex: 1;
            background: var(--light-gray);
            padding: 10px 15px;
            border-radius: 18px;
        }
        
        .comment-header {
            display: flex;
            justify-content: space-between;
            margin-bottom: 5px;
        }
        
        .comment-username {
            font-weight: 600;
            font-size: 14px;
        }
        
        .comment-time {
            font-size: 12px;
            color: var(--gray);
        }
        
        .comment-text {
            font-size: 14px;
            margin-bottom: 5px;
        }
        
        .comment-actions {
            display: flex;
            gap: 15px;
            font-size: 12px;
        }
        
        .comment-action {
            color: var(--gray);
            cursor: pointer;
            transition: color 0.3s;
        }
        
        .comment-action:hover {
            color: var(--primary);
        }
        
        /* 登录/注册模态框 */
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.5);
            z-index: 1000;
            align-items: center;
            justify-content: center;
        }
        
        .modal.show {
            display: flex;
        }
        
        .modal-content {
            background: white;
            border-radius: 10px;
            width: 100%;
            max-width: 400px;
            box-shadow: var(--shadow);
            overflow: hidden;
        }
        
        .modal-header {
            padding: 20px;
            background: var(--primary);
            color: white;
            position: relative;
            text-align: center;
        }
        
        .modal-close {
            position: absolute;
            top: 15px;
            right: 15px;
            background: none;
            border: none;
            color: white;
            font-size: 24px;
            cursor: pointer;
        }
        
        .modal-body {
            padding: 20px;
        }
        
        .tabs {
            display: flex;
            margin-bottom: 20px;
        }
        
        .tab {
            flex: 1;
            padding: 10px;
            text-align: center;
            background: var(--light-gray);
            border: none;
            cursor: pointer;
            font-weight: 500;
        }
        
        .tab.active {
            background: var(--primary);
            color: white;
        }
        
        .form-group {
            margin-bottom: 15px;
        }
        
        .form-group label {
            display: block;
            margin-bottom: 5px;
            font-weight: 500;
        }
        
        .form-group input {
            width: 100%;
            padding: 10px 15px;
            border: var(--border);
            border-radius: 6px;
            font-size: 16px;
        }
        
        .modal-footer {
            padding: 0 20px 20px;
            text-align: center;
        }
        
        .modal-footer p {
            margin-top: 15px;
            font-size: 14px;
            color: var(--gray);
        }
        
        .modal-footer a {
            color: var(--primary);
            text-decoration: none;
        }
        
        /* 响应式设计 */
        @media (max-width: 768px) {
            .main-content {
                grid-template-columns: 1fr;
            }
            
            .sidebar {
                display: none;
            }
            
            .navbar {
                flex-wrap: wrap;
            }
            
            .nav-links {
                order: 3;
                width: 100%;
                margin-top: 15px;
                justify-content: center;
            }
        }
    </style>
</head>
<body>
    <!-- 导航栏 -->
    <header>
        <div class="container">
            <nav class="navbar">
                <a href="#" class="logo">
                    <i class="fas fa-lightbulb"></i>
                    IdeaShare
                </a>
                
                <ul class="nav-links">
                    <li><a href="#" class="active">首页</a></li>
                    <li><a href="#">发现</a></li>
                    <li><a href="#">热门</a></li>
                    <li><a href="#">话题</a></li>
                </ul>
                
                <div class="user-actions">
                    <button class="btn btn-primary" id="loginBtn">登录</button>
                    <button class="btn btn-outline" id="registerBtn">注册</button>
                </div>
            </nav>
        </div>
    </header>
    
    <!-- 主内容区 -->
    <div class="container">
        <div class="main-content">
            <!-- 侧边栏 -->
            <aside class="sidebar">
                <h3>热门话题</h3>
                <ul class="trending-topics">
                    <li><a href="#"><i class="fas fa-hashtag"></i> 科技创新</a></li>
                    <li><a href="#"><i class="fas fa-hashtag"></i> 旅行摄影</a></li>
                    <li><a href="#"><i class="fas fa-hashtag"></i> 美食分享</a></li>
                    <li><a href="#"><i class="fas fa-hashtag"></i> 健身日常</a></li>
                    <li><a href="#"><i class="fas fa-hashtag"></i> 电影推荐</a></li>
                </ul>
            </aside>
            
            <!-- 内容区域 -->
            <main class="content-area">
                <!-- 创建卡片 -->
                <div class="create-card">
                    <textarea placeholder="分享你的想法..."></textarea>
                    <div class="media-upload">
                        <div class="upload-btn">
                            <i class="fas fa-image"></i> 图片
                        </div>
                        <div class="upload-btn">
                            <i class="fas fa-video"></i> 视频
                        </div>
                        <div class="upload-btn">
                            <i class="fas fa-map-marker-alt"></i> 地点
                        </div>
                    </div>
                    <button class="btn btn-primary">发布</button>
                </div>
                
                <!-- 帖子卡片 -->
                <div class="post-card">
                    <div class="post-header">
                        <div class="user-avatar">CZ</div>
                        <div class="user-info">
                            <div class="username">曹桢 (管理员)</div>
                            <div class="post-time">2小时前</div>
                        </div>
                        <div class="post-actions">
                            <button class="dropdown-btn">
                                <i class="fas fa-ellipsis-h"></i>
                            </button>
                            <div class="dropdown-content">
                                <button><i class="fas fa-edit"></i> 编辑</button>
                                <button><i class="fas fa-trash-alt"></i> 删除</button>
                            </div>
                        </div>
                    </div>
                    
                    <div class="post-content">
                        <div class="post-text">
                            今天发现了一个绝佳的摄影地点！这个地方的日落简直太美了，分享给大家看看。
                        </div>
                        <div class="post-media">
                            <img src="https://images.unsplash.com/photo-1501854140801-50d01698950b?ixlib=rb-4.0.3&auto=format&fit=crop&w=1200&q=80" alt="美丽的日落">
                        </div>
                    </div>
                    
                    <div class="post-stats">
                        <span><i class="fas fa-heart"></i> 128</span>
                        <span><i class="fas fa-comment"></i> 24</span>
                        <span><i class="fas fa-share"></i> 8</span>
                    </div>
                    
                    <div class="post-interactions">
                        <button class="interaction-btn">
                            <i class="far fa-heart"></i> 点赞
                        </button>
                        <button class="interaction-btn">
                            <i class="far fa-comment"></i> 评论
                        </button>
                        <button class="interaction-btn">
                            <i class="far fa-share-square"></i> 分享
                        </button>
                    </div>
                    
                    <div class="comments-section">
                        <div class="comment-form">
                            <input type="text" placeholder="写下你的评论...">
                            <button>发送</button>
                        </div>
                        
                        <div class="comment-list">
                            <!-- 评论示例 -->
                            <div class="comment">
                                <div class="comment-avatar">JL</div>
                                <div class="comment-content">
                                    <div class="comment-header">
                                        <div class="comment-username">李明</div>
                                        <div class="comment-time">1小时前</div>
                                    </div>
                                    <div class="comment-text">
                                        太美了！能分享一下具体位置吗？我也想去看看。
                                    </div>
                                    <div class="comment-actions">
                                        <span class="comment-action">点赞</span>
                                        <span class="comment-action">回复</span>
                                        <span class="comment-action">删除</span>
                                    </div>
                                </div>
                            </div>
                            
                            <div class="comment">
                                <div class="comment-avatar">WX</div>
                                <div class="comment-content">
                                    <div class="comment-header">
                                        <div class="comment-username">王欣</div>
                                        <div class="comment-time">45分钟前</div>
                                    </div>
                                    <div class="comment-text">
                                        照片拍得真棒！请问是用什么设备拍摄的？
                                    </div>
                                    <div class="comment-actions">
                                        <span class="comment-action">点赞</span>
                                        <span class="comment-action">回复</span>
                                        <span class="comment-action">删除</span>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
                
                <!-- 另一个帖子 -->
                <div class="post-card">
                    <div class="post-header">
                        <div class="user-avatar">ZS</div>
                        <div class="user-info">
                            <div class="username">张三</div>
                            <div class="post-time">5小时前</div>
                        </div>
                        <div class="post-actions">
                            <button class="dropdown-btn">
                                <i class="fas fa-ellipsis-h"></i>
                            </button>
                            <div class="dropdown-content">
                                <button><i class="fas fa-edit"></i> 编辑</button>
                                <button><i class="fas fa-trash-alt"></i> 删除</button>
                            </div>
                        </div>
                    </div>
                    
                    <div class="post-content">
                        <div class="post-text">
                            刚刚尝试了一道新菜谱，川味麻辣香锅，超级下饭！分享我的烹饪过程视频。
                        </div>
                        <div class="post-media">
                            <video controls poster="https://images.unsplash.com/photo-1563245372-f21724e3856d?ixlib=rb-4.0.3&auto=format&fit=crop&w=1200&q=80">
                                <source src="#" type="video/mp4">
                                您的浏览器不支持视频播放。
                            </video>
                        </div>
                    </div>
                    
                    <div class="post-stats">
                        <span><i class="fas fa-heart"></i> 89</span>
                        <span><i class="fas fa-comment"></i> 15</span>
                        <span><i class="fas fa-share"></i> 6</span>
                    </div>
                    
                    <div class="post-interactions">
                        <button class="interaction-btn">
                            <i class="far fa-heart"></i> 点赞
                        </button>
                        <button class="interaction-btn">
                            <i class="far fa-comment"></i> 评论
                        </button>
                        <button class="interaction-btn">
                            <i class="far fa-share-square"></i> 分享
                        </button>
                    </div>
                </div>
            </main>
        </div>
    </div>
    
    <!-- 登录/注册模态框 -->
    <div class="modal" id="authModal">
        <div class="modal-content">
            <div class="modal-header">
                <h2>欢迎来到想法分享社区</h2>
                <button class="modal-close">&times;</button>
            </div>
            <div class="modal-body">
                <div class="tabs">
                    <button class="tab active" id="loginTab">登录</button>
                    <button class="tab" id="registerTab">注册</button>
                </div>
                
                <form id="loginForm">
                    <div class="form-group">
                        <label for="username">用户名</label>
                        <input type="text" id="username" placeholder="输入用户名">
                    </div>
                    <div class="form-group">
                        <label for="password">密码</label>
                        <input type="password" id="password" placeholder="输入密码">
                    </div>
                    <button type="submit" class="btn btn-primary" style="width: 100%;">登录</button>
                </form>
                
                <form id="registerForm" style="display: none;">
                    <div class="form-group">
                        <label for="regUsername">用户名</label>
                        <input type="text" id="regUsername" placeholder="创建用户名">
                    </div>
                    <div class="form-group">
                        <label for="regEmail">电子邮箱</label>
                        <input type="email" id="regEmail" placeholder="输入邮箱">
                    </div>
                    <div class="form-group">
                        <label for="regPassword">密码</label>
                        <input type="password" id="regPassword" placeholder="创建密码">
                    </div>
                    <div class="form-group">
                        <label for="regConfirmPassword">确认密码</label>
                        <input type="password" id="regConfirmPassword" placeholder="再次输入密码">
                    </div>
                    <button type="submit" class="btn btn-primary" style="width: 100%;">注册</button>
                </form>
            </div>
            <div class="modal-footer">
                <p>继续即表示您同意我们的 <a href="#">服务条款</a> 和 <a href="#">隐私政策</a></p>
            </div>
        </div>
    </div>
    
    <script>
        // 页面加载时创建管理员账户
        document.addEventListener('DOMContentLoaded', function() {
            // 创建管理员账户
            const adminAccount = {
                username: 'caozhen',
                password: 'caozhen1',
                isAdmin: true
            };
            
            // 保存到本地存储
            if (!localStorage.getItem('adminAccount')) {
                localStorage.setItem('adminAccount', JSON.stringify(adminAccount));
            }
            
            // 模态框控制
            const authModal = document.getElementById('authModal');
            const loginBtn = document.getElementById('loginBtn');
            const registerBtn = document.getElementById('registerBtn');
            const modalClose = document.querySelector('.modal-close');
            const loginTab = document.getElementById('loginTab');
            const registerTab = document.getElementById('registerTab');
            const loginForm = document.getElementById('loginForm');
            const registerForm = document.getElementById('registerForm');
            
            // 打开登录模态框
            loginBtn.addEventListener('click', function() {
                authModal.classList.add('show');
                loginTab.classList.add('active');
                registerTab.classList.remove('active');
                loginForm.style.display = 'block';
                registerForm.style.display = 'none';
            });
            
            // 打开注册模态框
            registerBtn.addEventListener('click', function() {
                authModal.classList.add('show');
                registerTab.classList.add('active');
                loginTab.classList.remove('active');
                registerForm.style.display = 'block';
                loginForm.style.display = 'none';
            });
            
            // 关闭模态框
            modalClose.addEventListener('click', function() {
                authModal.classList.remove('show');
            });
            
            // 切换登录/注册标签
            loginTab.addEventListener('click', function() {
                loginTab.classList.add('active');
                registerTab.classList.remove('active');
                loginForm.style.display = 'block';
                registerForm.style.display = 'none';
            });
            
            registerTab.addEventListener('click', function() {
                registerTab.classList.add('active');
                loginTab.classList.remove('active');
                registerForm.style.display = 'block';
                loginForm.style.display = 'none';
            });
            
            // 登录表单提交
            loginForm.addEventListener('submit', function(e) {
                e.preventDefault();
                const username = document.getElementById('username').value;
                const password = document.getElementById('password').value;
                
                // 验证登录
                const adminAccount = JSON.parse(localStorage.getItem('adminAccount'));
                if (username === adminAccount.username && password === adminAccount.password) {
                    alert('管理员登录成功！');
                    authModal.classList.remove('show');
                    // 更新UI显示已登录状态
                    document.getElementById('loginBtn').style.display = 'none';
                    document.getElementById('registerBtn').style.display = 'none';
                    document.querySelector('.user-actions').innerHTML = `
                        <div class="user-avatar" style="width: 36px; height: 36px; margin-right: 10px;">CZ</div>
                        <button class="btn btn-outline">退出</button>
                    `;
                } else {
                    alert('用户名或密码错误！');
                }
            });
            
            // 注册表单提交
            registerForm.addEventListener('submit', function(e) {
                e.preventDefault();
                const username = document.getElementById('regUsername').value;
                const email = document.getElementById('regEmail').value;
                const password = document.getElementById('regPassword').value;
                const confirmPassword = document.getElementById('regConfirmPassword').value;
                
                if (password !== confirmPassword) {
                    alert('两次输入的密码不一致！');
                    return;
                }
                
                // 创建用户账户
                const newUser = {
                    username,
                    email,
                    password
                };
                
                // 保存用户数据
                let users = JSON.parse(localStorage.getItem('users')) || [];
                users.push(newUser);
                localStorage.setItem('users', JSON.stringify(users));
                
                alert('注册成功！请登录。');
                registerTab.classList.remove('active');
                loginTab.classList.add('active');
                registerForm.style.display = 'none';
                loginForm.style.display = 'block';
            });
            
            // 帖子操作下拉菜单
            const dropdownBtns = document.querySelectorAll('.dropdown-btn');
            dropdownBtns.forEach(btn => {
                btn.addEventListener('click', function() {
                    const dropdownContent = this.nextElementSibling;
                    dropdownContent.classList.toggle('show');
                });
            });
            
            // 关闭下拉菜单当点击其他地方
            window.addEventListener('click', function(e) {
                if (!e.target.matches('.dropdown-btn')) {
                    const dropdowns = document.querySelectorAll('.dropdown-content');
                    dropdowns.forEach(dropdown => {
                        if (dropdown.classList.contains('show')) {
                            dropdown.classList.remove('show');
                        }
                    });
                }
            });
        });
    </script>
</body>
</html>
