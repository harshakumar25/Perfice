// script.js
document.addEventListener('DOMContentLoaded', function() {
    // ======================
    // STATE MANAGEMENT
    // ======================
    const state = {
        user: null,
        sessionActive: false,
        timerInterval: null,
        timerRemaining: 0,
        timerDuration: 1500, // 25 minutes in seconds
        isTimerRunning: false,
        platforms: {},
        sessions: [],
        achievements: [],
        streaks: {
            overall: 0,
            leetcode: 0,
            tryhackme: 0,
            calendar: []
        },
        weeklyProgress: {
            labels: ['Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun'],
            points: [0, 0, 0, 0, 0, 0, 0]
        }
    };

    // ======================
    // INITIALIZATION
    // ======================
    function init() {
        // Check if user is already logged in
        const savedUser = localStorage.getItem('codeflow_user');
        if (savedUser) {
            state.user = JSON.parse(savedUser);
            loadUserData();
            showDashboard();
        } else {
            showWelcomeModal();
        }

        // Initialize event listeners
        setupEventListeners();
        // Initialize charts
        initCharts();
        // Generate sample data for demo
        generateDemoData();
    }

    // ======================
    // AUTHENTICATION
    // ======================
    function login() {
        const email = document.getElementById('loginEmail').value;
        const password = document.getElementById('loginPassword').value;

        if (!email || !password) {
            showNotification('Please fill in all fields', 'error');
            return;
        }

        // Simulate API call
        const users = JSON.parse(localStorage.getItem('codeflow_users') || '[]');
        const user = users.find(u => u.email === email && u.password === password);

        if (user) {
            state.user = user;
            localStorage.setItem('codeflow_user', JSON.stringify(user));
            loadUserData();
            showDashboard();
            showNotification('Login successful!', 'success');
            triggerConfetti();
        } else {
            showNotification('Invalid credentials', 'error');
        }
    }

    function register() {
        const firstName = document.getElementById('registerFirstName').value;
        const lastName = document.getElementById('registerLastName').value;
        const email = document.getElementById('registerEmail').value;
        const password = document.getElementById('registerPassword').value;
        const confirmPassword = document.getElementById('registerConfirmPassword').value;
        const acceptTerms = document.getElementById('acceptTerms').checked;

        if (!firstName || !lastName || !email || !password || !confirmPassword) {
            showNotification('Please fill in all fields', 'error');
            return;
        }

        if (password.length < 8) {
            showNotification('Password must be at least 8 characters', 'error');
            return;
        }

        if (password !== confirmPassword) {
            showNotification('Passwords do not match', 'error');
            return;
        }

        if (!acceptTerms) {
            showNotification('Please accept terms and conditions', 'error');
            return;
        }

        // Check if user already exists
        const users = JSON.parse(localStorage.getItem('codeflow_users') || '[]');
        if (users.some(u => u.email === email)) {
            showNotification('User already exists', 'error');
            return;
        }

        // Create new user
        const newUser = {
            id: Date.now(),
            firstName,
            lastName,
            email,
            password, // In real app, hash this!
            points: 100,
            level: 1,
            platforms: {},
            createdAt: new Date().toISOString()
        };

        users.push(newUser);
        localStorage.setItem('codeflow_users', JSON.stringify(users));
        localStorage.setItem('codeflow_user', JSON.stringify(newUser));

        state.user = newUser;
        loadUserData();
        showDashboard();
        showNotification('Account created successfully!', 'success');
        triggerConfetti();
    }

    function logout() {
        state.user = null;
        localStorage.removeItem('codeflow_user');
        showAuthScreen();
        showNotification('Logged out successfully', 'success');
    }

    function switchAuthTab(tab) {
        const loginForm = document.getElementById('loginForm');
        const registerForm = document.getElementById('registerForm');
        const loginTabBtn = document.getElementById('loginTabBtn');
        const registerTabBtn = document.getElementById('registerTabBtn');

        if (tab === 'login') {
            loginForm.classList.remove('hidden');
            registerForm.classList.add('hidden');
            loginTabBtn.classList.add('tab-active');
            loginTabBtn.classList.remove('text-gray-400');
            registerTabBtn.classList.remove('tab-active');
            registerTabBtn.classList.add('text-gray-400');
        } else {
            registerForm.classList.remove('hidden');
            loginForm.classList.add('hidden');
            registerTabBtn.classList.add('tab-active');
            registerTabBtn.classList.remove('text-gray-400');
            loginTabBtn.classList.remove('tab-active');
            loginTabBtn.classList.add('text-gray-400');
        }
    }

    // ======================
    // PLATFORM INTEGRATION
    // ======================
    function connectPlatform(platform) {
        const inputId = `${platform}Username`;
        const username = document.getElementById(inputId).value.trim();

        if (!username) {
            showNotification(`Please enter ${platform} username`, 'error');
            return;
        }

        // Save platform data
        state.user.platforms[platform] = { username, connectedAt: new Date().toISOString() };
        localStorage.setItem('codeflow_user', JSON.stringify(state.user));

        // Update UI
        updatePlatformDisplay(platform, username);
        showNotification(`${platform} connected successfully!`, 'success');

        // Fetch platform data (simulated)
        fetchPlatformData(platform, username);
    }

    function saveAllPlatforms() {
        const platforms = ['github', 'leetcode', 'tryhackme', 'codeforces'];
        let connectedCount = 0;

        platforms.forEach(platform => {
            const inputId = `${platform}Username`;
            const input = document.getElementById(inputId);
            if (input && input.value.trim()) {
                connectPlatform(platform);
                connectedCount++;
            }
        });

        if (connectedCount > 0) {
            showNotification(`Connected ${connectedCount} platform(s)`, 'success');
            closePlatformModal();
        } else {
            showNotification('No platforms connected', 'warning');
        }
    }

    function fetchPlatformData(platform, username) {
        // Simulated API responses
        const mockData = {
            github: {
                repos: Math.floor(Math.random() * 50) + 10,
                commits: Math.floor(Math.random() * 200) + 50,
                activity: Math.floor(Math.random() * 100)
            },
            leetcode: {
                solved: Math.floor(Math.random() * 500) + 100,
                rating: Math.floor(Math.random() * 2000) + 1000,
                rank: `Top ${Math.floor(Math.random() * 20) + 1}%`,
                streak: Math.floor(Math.random() * 30) + 1
            },
            tryhackme: {
                rooms: Math.floor(Math.random() * 100) + 20,
                points: Math.floor(Math.random() * 50000) + 10000,
                rank: ['Beginner', 'Script Kiddie', 'Hacker', 'Elite Hacker'][Math.floor(Math.random() * 4)]
            },
            codeforces: {
                rating: Math.floor(Math.random() * 2500) + 1000,
                contests: Math.floor(Math.random() * 100) + 10,
                rank: ['Newbie', 'Pupil', 'Specialist', 'Expert'][Math.floor(Math.random() * 4)]
            }
        };

        // Update UI with platform data
        setTimeout(() => {
            updatePlatformUI(platform, mockData[platform]);
            showNotification(`${platform} data synced!`, 'success');
        }, 1000);
    }

    function updatePlatformUI(platform, data) {
        const elements = {
            github: {
                repos: 'githubRepos',
                commits: 'githubCommits',
                activity: 'githubActivity',
                activityBar: 'githubActivityBar'
            },
            leetcode: {
                solved: 'leetcodeSolved',
                rating: 'leetcodeRating',
                rank: 'leetcodeRank',
                streak: 'leetcodeStreak',
                progressBar: 'leetcodeProgressBar'
            },
            tryhackme: {
                rooms: 'tryhackmeRooms',
                points: 'tryhackmePoints',
                rank: 'tryhackmeRank',
                streak: 'tryhackmeStreak',
                progressBar: 'tryhackmeProgressBar'
            },
            codeforces: {
                rating: 'codeforcesRating',
                contests: 'codeforcesContests',
                rank: 'codeforcesRank',
                progressBar: 'codeforcesProgressBar'
            }
        };






         //check forr the updated linked platform data    // check for updated linked plaatform then connect with codeflow pro
         // ????? need modifications

        if (elements[platform]) {
            Object.entries(data).forEach(([key, value]) => {
                const elementId = elements[platform][key];
                if (elementId) {
                    const element = document.getElementById(elementId);
                    if (element) {
                        if (key === 'activityBar' || key.includes('progressBar')) {
                            element.style.width = `${value}%`;
                        } else if (key === 'activity') {
                            element.textContent = `${value}%`;
                        } else {
                            element.textContent = value;
                        }
                    }
                }
            });
        }

        // Update streaks in quick stats
        if (platform === 'leetcode' && data.streak) {
            state.streaks.leetcode = data.streak;
            updateStreakDisplay();
        }
    }

    // ======================
    // STUDY SESSIONS & TIMER
    // ======================
    function startStudySession() {
        const topic = document.getElementById('sessionTopic').value.trim();
        const duration = parseInt(document.getElementById('sessionDuration').value) || 25;
        const platform = document.getElementById('sessionPlatform').value;
        const notes = document.getElementById('sessionNotes').value.trim();

        if (!topic) {
            showNotification('Please enter a study topic', 'error');
            return;
        }

        if (!platform) {
            showNotification('Please select a platform', 'error');
            return;
        }

        // Start timer
        state.timerDuration = duration * 60;
        state.timerRemaining = state.timerDuration;
        state.sessionActive = true;

        // Update timer modal
        document.getElementById('timerTopic').textContent = topic;
        document.getElementById('timerPlatform').textContent = platform.charAt(0).toUpperCase() + platform.slice(1);
        document.getElementById('timerDisplay').textContent = formatTime(state.timerRemaining);

        // Show timer modal
        showTimerModal();

        // Start timer automatically
        setTimeout(() => startTimer(), 1000);

        showNotification('Study session started!', 'success');
    }

    function startTimer() {
        if (state.isTimerRunning) return;

        state.isTimerRunning = true;
        document.getElementById('startTimerBtn').classList.add('hidden');
        document.getElementById('pauseTimerBtn').classList.remove('hidden');

        state.timerInterval = setInterval(() => {
            state.timerRemaining--;

            // Update display
            document.getElementById('timerDisplay').textContent = formatTime(state.timerRemaining);

            // Calculate progress
            const progress = ((state.timerDuration - state.timerRemaining) / state.timerDuration * 100).toFixed(1);
            document.getElementById('timerFocusPercent').textContent = `${progress}%`;

            // Check if timer finished
            if (state.timerRemaining <= 0) {
                finishTimer();
            }
        }, 1000);
    }

    function pauseTimer() {
        if (!state.isTimerRunning) return;

        state.isTimerRunning = false;
        clearInterval(state.timerInterval);
        document.getElementById('pauseTimerBtn').classList.add('hidden');
        document.getElementById('startTimerBtn').classList.remove('hidden');
    }

    function resetTimer() {
        pauseTimer();
        state.timerRemaining = state.timerDuration;
        document.getElementById('timerDisplay').textContent = formatTime(state.timerRemaining);
    }

    function finishTimer() {
        pauseTimer();

        // Award points
        const pointsEarned = Math.floor(state.timerDuration / 60 * 10); // 10 points per minute
        state.user.points += pointsEarned;
        
        // Check level up
        checkLevelUp();

        // Save session
        const session = {
            id: Date.now(),
            topic: document.getElementById('sessionTopic').value.trim(),
            platform: document.getElementById('sessionPlatform').value,
            duration: state.timerDuration / 60,
            points: pointsEarned,
            date: new Date().toISOString(),
            notes: document.getElementById('sessionNotes').value.trim()
        };

        state.sessions.unshift(session);
        updateSessionsDisplay();
        updateStreak();
        updateWeeklyProgress(pointsEarned);

        // Show completion message
        showNotification(`Session completed! Earned ${pointsEarned} points!`, 'success');
        triggerConfetti();

        // Close modal after delay
        setTimeout(() => {
            closeTimerModal();
            // Reset form
            document.getElementById('sessionTopic').value = '';
            document.getElementById('sessionNotes').value = '';
        }, 2000);
    }

    function setDuration(minutes) {
        document.getElementById('sessionDuration').value = minutes;
    }

    function setTimerDuration(minutes) {
        state.timerDuration = minutes * 60;
        state.timerRemaining = state.timerDuration;
        document.getElementById('timerDisplay').textContent = formatTime(state.timerRemaining);
    }

    // ======================
    // LEETCODE & TRYHACKME LOGGING
    // ======================
    function logLeetCode() {
        showLeetCodeModal();
    }

    function submitLeetCode() {
        const problem = document.getElementById('leetcodeProblem').value.trim();
        const difficulty = document.getElementById('leetcodeDifficulty').value;
        const time = parseInt(document.getElementById('leetcodeTime').value) || 30;
        const notes = document.getElementById('leetcodeNotes').value.trim();

        if (!problem) {
            showNotification('Please enter problem name', 'error');
            return;
        }

        // Award points based on difficulty
        const pointValues = { easy: 10, medium: 25, hard: 50 };
        const pointsEarned = pointValues[difficulty] || 10;

        state.user.points += pointsEarned;
        updateUserStats();

        // Update LeetCode stats
        const leetcodeSolved = document.getElementById('leetcodeSolved');
        const current = parseInt(leetcodeSolved.textContent) || 0;
        leetcodeSolved.textContent = current + 1;

        // Add to session history
        const session = {
            id: Date.now(),
            topic: `LeetCode: ${problem}`,
            platform: 'leetcode',
            duration: time,
            points: pointsEarned,
            date: new Date().toISOString(),
            notes: `${difficulty.charAt(0).toUpperCase() + difficulty.slice(1)} - ${notes}`
        };

        state.sessions.unshift(session);
        updateSessionsDisplay();
        updateStreak();
        updateWeeklyProgress(pointsEarned);

        showNotification(`LeetCode problem logged! +${pointsEarned} points`, 'success');
        closeLeetCodeModal();
        checkAchievements();
    }

    function logTryHackMe() {
        showTryHackMeModal();
    }

    function submitTryHackMe() {
        const room = document.getElementById('thmRoom').value.trim();
        const difficulty = document.getElementById('thmDifficulty').value;
        const time = parseInt(document.getElementById('thmTime').value) || 60;
        const progress = parseInt(document.getElementById('thmProgress').value) || 100;

        if (!room) {
            showNotification('Please enter room name', 'error');
            return;
        }

        // Award points
        const pointValues = { easy: 20, medium: 40, hard: 75, insane: 150 };
        const basePoints = pointValues[difficulty] || 20;
        const pointsEarned = Math.floor(basePoints * (progress / 100));

        state.user.points += pointsEarned;
        updateUserStats();

        // Update TryHackMe stats
        const thmRooms = document.getElementById('tryhackmeRooms');
        const current = parseInt(thmRooms.textContent) || 0;
        thmRooms.textContent = current + 1;

        // Add to session history
        const session = {
            id: Date.now(),
            topic: `TryHackMe: ${room}`,
            platform: 'tryhackme',
            duration: time,
            points: pointsEarned,
            date: new Date().toISOString(),
            notes: `${difficulty.charAt(0).toUpperCase() + difficulty.slice(1)} - ${progress}% complete`
        };

        state.sessions.unshift(session);
        updateSessionsDisplay();
        updateStreak();
        updateWeeklyProgress(pointsEarned);

        showNotification(`TryHackMe room logged! +${pointsEarned} points`, 'success');
        closeTryHackMeModal();
        checkAchievements();
    }

    // ======================
    // STREAKS & CALENDAR
    // ======================
    function updateStreak() {
        const today = new Date().toISOString().split('T')[0];
        
        // Check if already logged today
        if (!state.streaks.calendar.includes(today)) {
            state.streaks.calendar.push(today);
            state.streaks.overall++;
            
            // Update platform streaks if sessions exist today
            const todaySessions = state.sessions.filter(s => 
                s.date.startsWith(today) && s.platform
            );
            
            todaySessions.forEach(session => {
                if (session.platform === 'leetcode') state.streaks.leetcode++;
                if (session.platform === 'tryhackme') state.streaks.tryhackme++;
            });
        }

        updateStreakDisplay();
        generateStreakCalendar();
    }

    function generateStreakCalendar() {
        const container = document.getElementById('streakCalendar');
        container.innerHTML = '';

        // Generate last 49 days (7 weeks)
        for (let i = 48; i >= 0; i--) {
            const date = new Date();
            date.setDate(date.getDate() - i);
            const dateStr = date.toISOString().split('T')[0];
            
            const dot = document.createElement('div');
            dot.className = 'streak-dot';
            
            if (state.streaks.calendar.includes(dateStr)) {
                dot.classList.add('active');
                
                // Check if today
                const today = new Date().toISOString().split('T')[0];
                if (dateStr === today) {
                    dot.classList.add('today');
                }
            } else {
                dot.classList.add('inactive');
            }
            
            container.appendChild(dot);
        }

        // Update streak displays
        document.getElementById('mainStreak').textContent = `${state.streaks.overall} days`;
        document.getElementById('leetcodeStreak').textContent = `${state.streaks.leetcode} days`;
        document.getElementById('tryhackmeStreak').textContent = `${state.streaks.tryhackme} days`;
        document.getElementById('currentStreak').textContent = `${state.streaks.overall} days`;
    }

    // ======================
    // ACHIEVEMENTS
    // ======================
    function initAchievements() {
        state.achievements = [
            { id: 1, name: 'First Steps', description: 'Complete your first study session', icon: 'fa-rocket', unlocked: false, criteria: { type: 'sessions', value: 1 } },
            { id: 2, name: 'LeetCode Novice', description: 'Solve 10 LeetCode problems', icon: 'fa-leetcode', unlocked: false, criteria: { type: 'leetcode', value: 10 } },
            { id: 3, name: 'Hacker Initiate', description: 'Complete 5 TryHackMe rooms', icon: 'fa-shield-alt', unlocked: false, criteria: { type: 'tryhackme', value: 5 } },
            { id: 4, name: 'Week Warrior', description: 'Maintain a 7-day streak', icon: 'fa-fire', unlocked: false, criteria: { type: 'streak', value: 7 } },
            { id: 5, name: 'Point Master', description: 'Earn 1000 points', icon: 'fa-trophy', unlocked: false, criteria: { type: 'points', value: 1000 } },
            { id: 6, name: 'Platform Explorer', description: 'Connect all 4 platforms', icon: 'fa-plug', unlocked: false, criteria: { type: 'platforms', value: 4 } },
            { id: 7, name: 'Marathon Runner', description: 'Study for 10 hours total', icon: 'fa-running', unlocked: false, criteria: { type: 'hours', value: 10 } },
            { id: 8, name: 'Code Master', description: 'Reach Level 10', icon: 'fa-crown', unlocked: false, criteria: { type: 'level', value: 10 } }
        ];

        // Load unlocked achievements from storage
        const saved = localStorage.getItem('codeflow_achievements');
        if (saved) {
            const unlocked = JSON.parse(saved);
            state.achievements.forEach(achievement => {
                if (unlocked.includes(achievement.id)) {
                    achievement.unlocked = true;
                }
            });
        }

        renderAchievements();
    }

    function checkAchievements() {
        let unlockedNew = false;
        
        state.achievements.forEach(achievement => {
            if (!achievement.unlocked) {
                let conditionMet = false;
                
                switch (achievement.criteria.type) {
                    case 'sessions':
                        conditionMet = state.sessions.length >= achievement.criteria.value;
                        break;
                    case 'leetcode':
                        const leetcodeCount = state.sessions.filter(s => s.platform === 'leetcode').length;
                        conditionMet = leetcodeCount >= achievement.criteria.value;
                        break;
                    case 'tryhackme':
                        const thmCount = state.sessions.filter(s => s.platform === 'tryhackme').length;
                        conditionMet = thmCount >= achievement.criteria.value;
                        break;
                    case 'streak':
                        conditionMet = state.streaks.overall >= achievement.criteria.value;
                        break;
                    case 'points':
                        conditionMet = state.user.points >= achievement.criteria.value;
                        break;
                    case 'platforms':
                        const platformCount = Object.keys(state.user.platforms || {}).length;
                        conditionMet = platformCount >= achievement.criteria.value;
                        break;
                    case 'hours':
                        const totalHours = state.sessions.reduce((sum, session) => sum + (session.duration || 0), 0) / 60;
                        conditionMet = totalHours >= achievement.criteria.value;
                        break;
                    case 'level':
                        conditionMet = state.user.level >= achievement.criteria.value;
                        break;
                }
                
                if (conditionMet) {
                    achievement.unlocked = true;
                    unlockedNew = true;
                    
                    // Save to storage
                    const unlockedIds = state.achievements
                        .filter(a => a.unlocked)
                        .map(a => a.id);
                    localStorage.setItem('codeflow_achievements', JSON.stringify(unlockedIds));
                    
                    // Show notification
                    showNotification(`Achievement unlocked: ${achievement.name}!`, 'success');
                    triggerConfetti();
                }
            }
        });
        
        if (unlockedNew) {
            renderAchievements();
        }
    }

    function renderAchievements() {
        const container = document.getElementById('achievementsGrid');
        container.innerHTML = '';
        
        const unlockedCount = state.achievements.filter(a => a.unlocked).length;
        document.getElementById('achievementsCount').textContent = `${unlockedCount} unlocked`;
        
        state.achievements.forEach(achievement => {
            const card = document.createElement('div');
            card.className = `p-4 rounded-xl border ${achievement.unlocked ? 'border-yellow-400/30 bg-yellow-400/5' : 'border-gray-700 bg-white/2'}`;
            
            card.innerHTML = `
                <div class="flex items-center gap-3">
                    <div class="w-12 h-12 ${achievement.unlocked ? 'bg-gradient-to-r from-yellow-500 to-amber-500' : 'bg-gray-800'} rounded-lg flex items-center justify-center">
                        <i class="fas ${achievement.icon} ${achievement.unlocked ? 'text-white' : 'text-gray-400'}"></i>
                    </div>
                    <div class="flex-1">
                        <h4 class="font-bold ${achievement.unlocked ? 'text-yellow-300' : 'text-gray-300'}">${achievement.name}</h4>
                        <p class="text-sm ${achievement.unlocked ? 'text-yellow-400/80' : 'text-gray-400'}">${achievement.description}</p>
                    </div>
                    <div class="${achievement.unlocked ? 'text-yellow-400' : 'text-gray-600'}">
                        <i class="fas ${achievement.unlocked ? 'fa-unlock' : 'fa-lock'}"></i>
                    </div>
                </div>
            `;
            
            container.appendChild(card);
        });
    }

    // ======================
    // CHARTS
    // ======================
    let weeklyChart = null;

    function initCharts() {
        const ctx = document.getElementById('weeklyChart').getContext('2d');
        
        weeklyChart = new Chart(ctx, {
            type: 'line',
            data: {
                labels: state.weeklyProgress.labels,
                datasets: [{
                    label: 'Points',
                    data: state.weeklyProgress.points,
                    borderColor: '#6366f1',
                    backgroundColor: 'rgba(99, 102, 241, 0.1)',
                    borderWidth: 2,
                    fill: true,
                    tension: 0.4
                }]
            },
            options: {
                responsive: true,
                maintainAspectRatio: false,
                plugins: {
                    legend: {
                        display: false
                    }
                },
                scales: {
                    y: {
                        beginAtZero: true,
                        grid: {
                            color: 'rgba(255, 255, 255, 0.1)'
                        },
                        ticks: {
                            color: '#94a3b8'
                        }
                    },
                    x: {
                        grid: {
                            display: false
                        },
                        ticks: {
                            color: '#94a3b8'
                        }
                    }
                }
            }
        });
    }

    function updateWeeklyProgress(points) {
        const today = new Date().getDay();
        const adjustedDay = today === 0 ? 6 : today - 1; // Convert to 0-6 where 0=Monday
        
        state.weeklyProgress.points[adjustedDay] += points;
        
        if (weeklyChart) {
            weeklyChart.data.datasets[0].data = state.weeklyProgress.points;
            weeklyChart.update();
        }
        
        document.getElementById('weeklyPoints').textContent = `${state.weeklyProgress.points.reduce((a, b) => a + b, 0)} points`;
    }

    // ======================
    // UI UPDATES
    // ======================
    function updateUserStats() {
        if (!state.user) return;

        // Update level based on points
        const newLevel = Math.floor(state.user.points / 100) + 1;
        if (newLevel > state.user.level) {
            state.user.level = newLevel;
            document.getElementById('navLevel').classList.add('level-up');
            setTimeout(() => {
                document.getElementById('navLevel').classList.remove('level-up');
            }, 500);
            showNotification(`Level up! You're now level ${newLevel}`, 'success');
        }

        // Update UI elements
        document.getElementById('navPoints').textContent = state.user.points.toLocaleString();
        document.getElementById('navLevel').textContent = state.user.level;
        document.getElementById('navLevelBadge').textContent = state.user.level;
        document.getElementById('navUserName').textContent = state.user.firstName;
        document.getElementById('dropdownUserName').textContent = `${state.user.firstName} ${state.user.lastName}`;
        document.getElementById('dropdownUserEmail').textContent = state.user.email;
        document.getElementById('userGreeting').textContent = `Welcome back, ${state.user.firstName}!`;
        
        // Update progress bars
        const levelProgress = (state.user.points % 100) / 100 * 100;
        document.getElementById('userProgressBar').style.width = `${levelProgress}%`;
        document.getElementById('levelProgressBar').style.width = `${levelProgress}%`;
        document.getElementById('levelProgressText').textContent = `${levelProgress.toFixed(0)}%`;
        
        const pointsProgress = Math.min(state.user.points / 1000 * 100, 100);
        document.getElementById('pointsProgressBar').style.width = `${pointsProgress}%`;
        document.getElementById('pointsProgressText').textContent = `${state.user.points}/1000`;

        // Save updated user
        localStorage.setItem('codeflow_user', JSON.stringify(state.user));
    }

    function updateSessionsDisplay() {
        const recentContainer = document.getElementById('recentSessions');
        const historyContainer = document.getElementById('sessionHistory');

        // Sort sessions by date (newest first)
        const sortedSessions = [...state.sessions].sort((a, b) => new Date(b.date) - new Date(a.date));

        // Update recent sessions (last 3)
        recentContainer.innerHTML = '';
        const recentSessions = sortedSessions.slice(0, 3);
        
        if (recentSessions.length === 0) {
            recentContainer.innerHTML = `
                <div class="text-center py-8 text-gray-500">
                    <i class="fas fa-clock text-2xl mb-2 opacity-30"></i>
                    <p class="text-sm">No sessions yet</p>
                </div>
            `;
        } else {
            recentSessions.forEach(session => {
                const sessionEl = document.createElement('div');
                sessionEl.className = 'flex items-center justify-between p-3 bg-white/2 rounded-lg';
                sessionEl.innerHTML = `
                    <div>
                        <div class="font-medium">${session.topic.substring(0, 30)}${session.topic.length > 30 ? '...' : ''}</div>
                        <div class="text-xs text-gray-400">${formatDate(session.date)}</div>
                    </div>
                    <div class="text-right">
                        <div class="font-bold text-green-400">+${session.points}</div>
                        <div class="text-xs text-gray-400">${session.duration} min</div>
                    </div>
                `;
                recentContainer.appendChild(sessionEl);
            });
        }

        // Update session history table
        historyContainer.innerHTML = '';
        if (sortedSessions.length === 0) {
            historyContainer.innerHTML = `
                <tr>
                    <td colspan="6" class="py-8 text-center text-gray-500">
                        <i class="fas fa-history text-2xl mb-2 opacity-30"></i>
                        <p>No sessions recorded yet</p>
                    </td>
                </tr>
            `;
        } else {
            sortedSessions.forEach(session => {
                const row = document.createElement('tr');
                row.className = 'border-b border-white/5 hover:bg-white/2';
                row.innerHTML = `
                    <td class="py-3">${formatDate(session.date)}</td>
                    <td class="py-3 font-medium">${session.topic}</td>
                    <td class="py-3">
                        <span class="badge ${getPlatformBadgeClass(session.platform)}">
                            ${session.platform}
                        </span>
                    </td>
                    <td class="py-3">${session.duration} min</td>
                    <td class="py-3 font-bold text-green-400">+${session.points}</td>
                    <td class="py-3">
                        <button onclick="deleteSession(${session.id})" class="text-red-400 hover:text-red-300">
                            <i class="fas fa-trash"></i>
                        </button>
                    </td>
                `;
                historyContainer.appendChild(row);
            });
        }

        // Update today's focus time
        const today = new Date().toISOString().split('T')[0];
        const todayDuration = state.sessions
            .filter(s => s.date.startsWith(today))
            .reduce((sum, session) => sum + (session.duration || 0), 0);
        
        const hours = Math.floor(todayDuration / 60);
        const minutes = todayDuration % 60;
        document.getElementById('todayFocus').textContent = `${hours}h ${minutes}m`;
    }

    function updatePlatformDisplay(platform, username) {
        const displayElement = document.getElementById(`${platform}UsernameDisplay`);
        if (displayElement) {
            displayElement.textContent = username;
            displayElement.classList.remove('text-gray-400');
            displayElement.classList.add('text-green-400');
        }
    }

    // ======================
    // VIEW MANAGEMENT
    // ======================
    function showWelcomeModal() {
        document.getElementById('welcomeModal').style.display = 'flex';
        setTimeout(() => {
            document.getElementById('welcomeModal').style.opacity = '1';
        }, 10);
    }

    function closeWelcomeModal() {
        document.getElementById('welcomeModal').style.opacity = '0';
        setTimeout(() => {
            document.getElementById('welcomeModal').style.display = 'none';
            showAuthScreen();
        }, 300);
    }

    function showAuthScreen() {
        document.getElementById('authScreen').classList.remove('hidden');
        document.getElementById('dashboard').classList.add('hidden');
    }

    function showDashboard() {
        document.getElementById('authScreen').classList.add('hidden');
        document.getElementById('dashboard').classList.remove('hidden');
        updateUserStats();
        updateSessionsDisplay();
        generateStreakCalendar();
        initAchievements();
        checkAchievements();
    }

    function showPlatformModal() {
        document.getElementById('platformModal').classList.remove('hidden');
    }

    function closePlatformModal() {
        document.getElementById('platformModal').classList.add('hidden');
    }

    function showTimerModal() {
        document.getElementById('timerModal').classList.remove('hidden');
    }

    function closeTimerModal() {
        document.getElementById('timerModal').classList.add('hidden');
        pauseTimer();
        state.sessionActive = false;
    }

    function showLeetCodeModal() {
        document.getElementById('leetcodeModal').classList.remove('hidden');
    }

    function closeLeetCodeModal() {
        document.getElementById('leetcodeModal').classList.add('hidden');
        // Reset form
        document.getElementById('leetcodeProblem').value = '';
        document.getElementById('leetcodeNotes').value = '';
    }

    function showTryHackMeModal() {
        document.getElementById('tryhackmeModal').classList.remove('hidden');
    }

    function closeTryHackMeModal() {
        document.getElementById('tryhackmeModal').classList.add('hidden');
        // Reset form
        document.getElementById('thmRoom').value = '';
    }

    // ======================
    // UTILITY FUNCTIONS
    // ======================
    function formatTime(seconds) {
        const mins = Math.floor(seconds / 60);
        const secs = seconds % 60;
        return `${mins.toString().padStart(2, '0')}:${secs.toString().padStart(2, '0')}`;
    }

    function formatDate(dateString) {
        const date = new Date(dateString);
        return date.toLocaleDateString('en-US', { 
            month: 'short', 
            day: 'numeric',
            hour: '2-digit',
            minute: '2-digit'
        });
    }

    function showNotification(message, type = 'info') {
        // Create notification element
        const notification = document.createElement('div');
        notification.className = `fixed top-4 right-4 z-50 px-6 py-3 rounded-lg shadow-lg border transform translate-x-full transition-transform duration-300 ${
            type === 'success' ? 'bg-green-900/90 border-green-700 text-green-100' :
            type === 'error' ? 'bg-red-900/90 border-red-700 text-red-100' :
            type === 'warning' ? 'bg-yellow-900/90 border-yellow-700 text-yellow-100' :
            'bg-blue-900/90 border-blue-700 text-blue-100'
        }`;
        
        notification.innerHTML = `
            <div class="flex items-center gap-2">
                <i class="fas ${
                    type === 'success' ? 'fa-check-circle' :
                    type === 'error' ? 'fa-exclamation-circle' :
                    type === 'warning' ? 'fa-exclamation-triangle' :
                    'fa-info-circle'
                }"></i>
                <span>${message}</span>
            </div>
        `;
        
        document.body.appendChild(notification);
        
        // Animate in
        setTimeout(() => {
            notification.style.transform = 'translateX(0)';
        }, 10);
        
        // Remove after delay
        setTimeout(() => {
            notification.style.transform = 'translateX(100%)';
            setTimeout(() => {
                document.body.removeChild(notification);
            }, 300);
        }, 3000);
    }

    function triggerConfetti() {
        confetti({
            particleCount: 100,
            spread: 70,
            origin: { y: 0.6 },
            colors: ['#6366f1', '#8b5cf6', '#10b981', '#f59e0b', '#3b82f6']
        });
    }

    function getPlatformBadgeClass(platform) {
        const classes = {
            leetcode: 'badge-warning',
            tryhackme: 'badge-danger',
            codeforces: 'badge-info',
            github: 'badge-success'
        };
        return classes[platform] || 'badge-success';
    }

    function loadUserData() {
        // Load user data from localStorage
        const savedSessions = localStorage.getItem(`codeflow_sessions_${state.user.id}`);
        if (savedSessions) {
            state.sessions = JSON.parse(savedSessions);
        }

        const savedStreaks = localStorage.getItem(`codeflow_streaks_${state.user.id}`);
        if (savedStreaks) {
            state.streaks = JSON.parse(savedStreaks);
        }

        const savedWeekly = localStorage.getItem(`codeflow_weekly_${state.user.id}`);
        if (savedWeekly) {
            state.weeklyProgress = JSON.parse(savedWeekly);
        }
    }

    function saveUserData() {
        // Save user data to localStorage
        localStorage.setItem(`codeflow_sessions_${state.user.id}`, JSON.stringify(state.sessions));
        localStorage.setItem(`codeflow_streaks_${state.user.id}`, JSON.stringify(state.streaks));
        localStorage.setItem(`codeflow_weekly_${state.user.id}`, JSON.stringify(state.weeklyProgress));
    }

    function generateDemoData() {
        // Only generate demo data if no user data exists
        if (state.sessions.length === 0 && state.user) {
            // Generate some demo sessions
            const platforms = ['leetcode', 'tryhackme', 'codeforces', 'github'];
            const topics = [
                'Array Problems Practice',
                'Dynamic Programming Basics',
                'Web Security Fundamentals',
                'Data Structures Review',
                'Algorithm Optimization',
                'Network Protocols',
                'System Design Basics'
            ];

            for (let i = 0; i < 7; i++) {
                const date = new Date();
                date.setDate(date.getDate() - i);
                
                const platform = platforms[Math.floor(Math.random() * platforms.length)];
                const session = {
                    id: Date.now() + i,
                    topic: topics[Math.floor(Math.random() * topics.length)],
                    platform: platform,
                    duration: [25, 45, 60, 90][Math.floor(Math.random() * 4)],
                    points: [10, 25, 50, 100][Math.floor(Math.random() * 4)],
                    date: date.toISOString(),
                    notes: 'Demo session for testing'
                };
                state.sessions.push(session);
            }

            // Generate demo streaks
            for (let i = 0; i < 14; i++) {
                const date = new Date();
                date.setDate(date.getDate() - i);
                if (Math.random() > 0.3) {
                    state.streaks.calendar.push(date.toISOString().split('T')[0]);
                }
            }
            state.streaks.overall = state.streaks.calendar.length;
            state.streaks.leetcode = Math.floor(state.streaks.overall * 0.7);
            state.streaks.tryhackme = Math.floor(state.streaks.overall * 0.5);

            // Generate weekly progress
            state.weeklyProgress.points = state.weeklyProgress.points.map(() => 
                Math.floor(Math.random() * 200)
            );

            saveUserData();
        }
    }

    function checkLevelUp() {
        const oldLevel = state.user.level;
        const newLevel = Math.floor(state.user.points / 100) + 1;
        
        if (newLevel > oldLevel) {
            state.user.level = newLevel;
            showNotification(`🎉 Level Up! You reached Level ${newLevel}!`, 'success');
            triggerConfetti();
        }
    }

    function deleteSession(sessionId) {
        if (confirm('Are you sure you want to delete this session?')) {
            state.sessions = state.sessions.filter(s => s.id !== sessionId);
            updateSessionsDisplay();
            saveUserData();
            showNotification('Session deleted', 'success');
        }
    }

    function setupEventListeners() {
        // Platform progress slider
        const progressSlider = document.getElementById('thmProgress');
        if (progressSlider) {
            progressSlider.addEventListener('input', function() {
                document.getElementById('thmProgressValue').textContent = `${this.value}%`;
            });
        }

        // Auto-save user data
        window.addEventListener('beforeunload', saveUserData);
    }

    // ======================
    // PUBLIC FUNCTIONS (for HTML onclick)
    // ======================
    window.login = login;
    window.register = register;
    window.switchAuthTab = switchAuthTab;
    window.logout = logout;
    window.connectPlatform = connectPlatform;
    window.saveAllPlatforms = saveAllPlatforms;
    window.openPlatformModal = showPlatformModal;
    window.closePlatformModal = closePlatformModal;
    window.startStudySession = startStudySession;
    window.setDuration = setDuration;
    window.startTimer = startTimer;
    window.pauseTimer = pauseTimer;
    window.resetTimer = resetTimer;
    window.setTimerDuration = setTimerDuration;
    window.closeTimerModal = closeTimerModal;
    window.logLeetCode = logLeetCode;
    window.submitLeetCode = submitLeetCode;
    window.closeLeetCodeModal = closeLeetCodeModal;
    window.logTryHackMe = logTryHackMe;
    window.submitTryHackMe = submitTryHackMe;
    window.closeTryHackMeModal = closeTryHackMeModal;
    window.closeWelcomeModal = closeWelcomeModal;
    window.openGitHub = () => window.open('https://github.com', '_blank');
    window.openLeetCode = () => window.open('https://leetcode.com', '_blank');
    window.openTryHackMe = () => window.open('https://tryhackme.com', '_blank');
    window.openCodeforces = () => window.open('https://codeforces.com', '_blank');
    window.resetPassword = () => showNotification('Password reset link sent to your email', 'info');
    window.showTerms = () => showNotification('Terms and conditions modal would open here', 'info');
    window.showPrivacy = () => showNotification('Privacy policy modal would open here', 'info');
    window.deleteSession = deleteSession;

    // Initialize the application
    init();
});
