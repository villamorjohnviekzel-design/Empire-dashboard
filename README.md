<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>JV Digital - Personal Dashboard</title>
    <script src="https://cdn.jsdelivr.net/npm/@tailwindcss/browser@4"></script>
    <script src="https://unpkg.com/lucide@latest"></script>
    <link rel="manifest" href="data:application/manifest+json,%7B%22name%22%3A%22JV%20Digital%20Dashboard%22%2C%22short_name%22%3A%22JV%20Digital%22%2C%22start_url%22%3A%22.%22%2C%22display%22%3A%22standalone%22%2C%22background_color%22%3A%22%2309090b%22%2C%22theme_color%22%3A%22%23a855f7%22%2C%22icons%22%3A%5B%7B%22src%22%3A%22https%3A%2F%2Fimg.icons8.com%2Ffluent-systems-filled%2F512%2Fffffff%2Fartificial-intelligence.png%22%2C%22sizes%22%3A%22512x512%22%2C%22type%22%3A%22image%22%7D%5D%7D">
    
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@300;400;500;600;700&display=swap');
        
        body {
            font-family: 'Plus Jakarta Sans', sans-serif;
            background-color: #09090b;
            color: #f4f4f5;
        }

        /* Smooth custom scrolling */
        ::-webkit-scrollbar {
            width: 6px;
            height: 6px;
        }
        ::-webkit-scrollbar-track {
            background: #18181b;
        }
        ::-webkit-scrollbar-thumb {
            background: #3f3f46;
            border-radius: 3px;
        }

        /* Glassmorphism utility */
        .glass-card {
            background: rgba(24, 24, 27, 0.75);
            backdrop-filter: blur(12px);
            border: 1px solid rgba(63, 63, 70, 0.4);
        }

        /* Glow effects */
        .glow-purple {
            box-shadow: 0 0 20px rgba(168, 85, 247, 0.15);
        }

        /* Tab switching animation transition */
        .tab-content {
            display: none;
            opacity: 0;
            transform: translateY(10px);
            transition: opacity 0.3s ease, transform 0.3s ease;
        }
        .tab-content.active {
            display: block;
            opacity: 1;
            transform: translateY(0);
        }
    </style>
</head>
<body class="pb-24 md:pb-6 min-h-screen">

    <div class="fixed top-0 left-1/2 -translate-x-1/2 w-full max-w-7xl h-1 bg-gradient-to-r from-cyan-500 via-purple-500 to-pink-500 z-50"></div>

    <div class="max-w-md mx-auto px-4 pt-6 md:max-w-5xl md:py-8">
        
        <header class="flex items-center justify-between mb-8">
            <div>
                <h1 class="text-2xl font-bold tracking-tight bg-gradient-to-r from-white via-zinc-200 to-zinc-400 bg-clip-text text-transparent">JV DIGITAL</h1>
                <p class="text-xs text-zinc-400 flex items-center gap-1 mt-0.5"><i data-lucide="zap" class="w-3 h-3 text-purple-400"></i> Business Control Center</p>
            </div>
            <div id="pwa-install-container" class="hidden">
                <button id="btn-install" class="flex items-center gap-1.5 px-3 py-1.5 bg-purple-600/20 text-purple-400 border border-purple-500/30 rounded-xl text-xs font-medium animate-pulse">
                    <i data-lucide="download" class="w-3.5 h-3.5"></i> Install App
                </button>
            </div>
        </header>

        <section id="tab-dashboard" class="tab-content active space-y-6">
            
            <div class="glass-card glow-purple rounded-3xl p-6 relative overflow-hidden">
                <div class="absolute top-0 right-0 -mt-4 -mr-4 w-24 h-24 bg-purple-500/10 blur-xl rounded-full"></div>
                <div class="flex items-center gap-3 mb-3">
                    <div class="p-2 bg-purple-500/10 rounded-xl border border-purple-500/20 text-purple-400">
                        <i data-lucide="target" class="w-5 h-5"></i>
                    </div>
                    <span class="text-xs font-semibold tracking-widest text-purple-400 uppercase">Core Vision</span>
                </div>
                <p class="text-xl font-medium text-white leading-relaxed">
                    "Build an AI-powered digital empire."
                </p>
            </div>

            <div class="glass-card rounded-3xl p-6">
                <div class="flex justify-between items-center mb-3">
                    <div class="flex items-center gap-2">
                        <i data-lucide="trending-up" class="w-4 h-4 text-cyan-400"></i>
                        <h3 class="text-sm font-semibold text-zinc-200">Overall Roadmap Progress</h3>
                    </div>
                    <span id="global-progress-txt" class="text-sm font-bold text-cyan-400">0%</span>
                </div>
                <div class="w-full bg-zinc-800 h-2.5 rounded-full overflow-hidden">
                    <div id="global-progress-bar" class="bg-gradient-to-r from-cyan-500 to-purple-500 h-full transition-all duration-500" style="width: 0%"></div>
                </div>
            </div>

            <div class="glass-card rounded-3xl p-6 border-l-4 border-l-pink-500">
                <div class="flex items-start gap-3">
                    <i data-lucide="quote" class="w-5 h-5 text-pink-500 shrink-0 mt-1"></i>
                    <div>
                        <p id="motivational-quote" class="text-zinc-300 italic text-sm">"The best way to predict the future is to automate it."</p>
                        <span id="quote-author" class="block text-xs text-zinc-500 mt-2 font-medium">— JV Digital Systems</span>
                    </div>
                </div>
            </div>

            <div class="grid grid-cols-2 gap-4">
                <div class="glass-card rounded-2xl p-4 flex items-center gap-3">
                    <div class="p-2.5 bg-emerald-500/10 text-emerald-400 border border-emerald-500/20 rounded-xl">
                        <i data-lucide="check-square" class="w-4 h-4"></i>
                    </div>
                    <div>
                        <span class="text-xs text-zinc-400 block">Tasks Done</span>
                        <span id="stat-tasks" class="text-base font-bold text-white">0</span>
                    </div>
                </div>
                <div class="glass-card rounded-2xl p-4 flex items-center gap-3">
                    <div class="p-2.5 bg-amber-500/10 text-amber-400 border border-amber-500/20 rounded-xl">
                        <i data-lucide="book-open" class="w-4 h-4"></i>
                    </div>
                    <div>
                        <span class="text-xs text-zinc-400 block">Total Notes</span>
                        <span id="stat-notes" class="text-base font-bold text-white">0</span>
                    </div>
                </div>
            </div>
        </section>

        <section id="tab-roadmap" class="tab-content space-y-4">
            <h2 class="text-lg font-bold text-white mb-2 flex items-center gap-2"><i data-lucide="map" class="w-4 h-4 text-purple-400"></i> Strategic Milestones</h2>
            <div id="roadmap-accordion-container" class="space-y-3">
                </div>
        </section>

        <section id="tab-skills" class="tab-content space-y-4">
            <h2 class="text-lg font-bold text-white mb-2 flex items-center gap-2"><i data-lucide="award" class="w-4 h-4 text-purple-400"></i> Skill Matrix</h2>
            <div class="glass-card rounded-3xl p-5 space-y-5" id="skills-container">
                </div>
        </section>

        <section id="tab-tasks-mgr" class="tab-content space-y-4">
            <h2 class="text-lg font-bold text-white mb-2 flex items-center gap-2"><i data-lucide="list-todo" class="w-4 h-4 text-purple-400"></i> Quick Task Manager</h2>
            
            <form id="todo-form" class="flex gap-2">
                <input type="text" id="todo-input" placeholder="Add an urgent action item..." class="flex-1 bg-zinc-900 border border-zinc-700 rounded-xl px-4 py-3 text-sm focus:outline-none focus:border-purple-500 text-white placeholder-zinc-500" required>
                <button type="submit" class="bg-purple-600 hover:bg-purple-700 text-white px-4 rounded-xl flex items-center justify-center transition-colors">
                    <i data-lucide="plus" class="w-5 h-5"></i>
                </button>
            </form>

            <div id="todo-list" class="space-y-2 pt-2">
                </div>
        </section>

        <section id="tab-notes" class="tab-content space-y-4">
            <h2 class="text-lg font-bold text-white mb-2 flex items-center gap-2"><i data-lucide="notebook" class="w-4 h-4 text-purple-400"></i> Idea Engine & Notes</h2>
            
            <div class="glass-card rounded-2xl p-4 space-y-3">
                <input type="text" id="note-title" placeholder="Idea Title (e.g., Cold Outreach Strategy)" class="w-full bg-zinc-900/50 border border-zinc-700/60 rounded-xl px-3 py-2 text-sm focus:outline-none focus:border-purple-500 text-white">
                <textarea id="note-content" rows="3" placeholder="Flesh out your vision, business ideas, or strategies here..." class="w-full bg-zinc-900/50 border border-zinc-700/60 rounded-xl px-3 py-2 text-sm focus:outline-none focus:border-purple-500 text-white resize-none"></textarea>
                <button id="save-note-btn" class="w-full bg-zinc-800 hover:bg-zinc-700 border border-zinc-700 text-zinc-200 py-2.5 rounded-xl text-xs font-semibold uppercase tracking-wider flex items-center justify-center gap-2 transition-colors">
                    <i data-lucide="save" class="w-3.5 h-3.5"></i> Save Entry
                </button>
            </div>

            <div id="notes-grid" class="grid grid-cols-1 gap-3 pt-2">
                </div>
        </section>

    </div>

    <nav class="fixed bottom-0 left-0 right-0 bg-zinc-950/80 backdrop-filter backdrop-blur-xl border-t border-zinc-800/80 z-40 px-2 py-2 md:max-w-xl md:mx-auto md:bottom-4 md:rounded-2xl md:border shadow-2xl">
        <div class="flex justify-around items-center">
            <button onclick="switchTab('dashboard')" class="nav-btn flex flex-col items-center justify-center py-2 px-3 rounded-xl text-purple-500" data-tab="dashboard">
                <i data-lucide="layout-dashboard" class="w-5 h-5"></i>
                <span class="text-[10px] font-medium mt-1">Home</span>
            </button>
            <button onclick="switchTab('roadmap')" class="nav-btn flex flex-col items-center justify-center py-2 px-3 rounded-xl text-zinc-500" data-tab="roadmap">
                <i data-lucide="milestone" class="w-5 h-5"></i>
                <span class="text-[10px] font-medium mt-1">Roadmap</span>
            </button>
            <button onclick="switchTab('skills')" class="nav-btn flex flex-col items-center justify-center py-2 px-3 rounded-xl text-zinc-500" data-tab="skills">
                <i data-lucide="sliders" class="w-5 h-5"></i>
                <span class="text-[10px] font-medium mt-1">Skills</span>
            </button>
            <button onclick="switchTab('tasks-mgr')" class="nav-btn flex flex-col items-center justify-center py-2 px-3 rounded-xl text-zinc-500" data-tab="tasks-mgr">
                <i data-lucide="check-square" class="w-5 h-5"></i>
                <span class="text-[10px] font-medium mt-1">Tasks</span>
            </button>
            <button onclick="switchTab('notes')" class="nav-btn flex flex-col items-center justify-center py-2 px-3 rounded-xl text-zinc-500" data-tab="notes">
                <i data-lucide="pen-tool" class="w-5 h-5"></i>
                <span class="text-[10px] font-medium mt-1">Notes</span>
            </button>
        </div>
    </nav>

    <script>
        // --- 1. DATA STRUCTURES & STATIC CONTENT ---
        const initialRoadmapData = [
            { id: 1, title: "Phase 1: Foundation", goals: "Establish core brand identity and productivity workflows.", skills: "Canva, Notion setups", tasks: ["Set up business workspace", "Draft agency core service offer", "Design JV Digital logo concept"], deadline: "Month 1", notes: "Focus heavily on operational clarity." },
            { id: 2, title: "Phase 2: First Clients", goals: "Secure organic client acquisition and construct case studies.", skills: "Sales, Outreach Strategy", tasks: ["Build a list of 50 local business prospects", "Send personalized outreach scripts", "Close first retainer client"], deadline: "Month 2", notes: "Prioritize local modern service needs." },
            { id: 3, title: "Phase 3: Personal Website", goals: "Launch high-converting design or operations portfolio.", skills: "Web Development, UI/UX UI styling", tasks: ["Design portfolio landing page layout", "Optimize site speed and copy content", "Publish live domain links"], deadline: "Month 3", notes: "Ensure flawless presentation on mobile phones." },
            { id: 4, title: "Phase 4: AI Automation", goals: "Incorporate AI builds and system connections directly into offers.", skills: "ChatGPT, Claude, Make.com, ManyChat", tasks: ["Build automated lead capture chat framework", "Construct internal workflows for onboarding", "Create client-facing AI discovery prototype"], deadline: "Month 5", notes: "Position AI automation as a major efficiency upgrade." },
            { id: 5, title: "Phase 5: Agency Growth", goals: "Delegate low-leverage execution tasks and optimize conversions.", skills: "Meta Ads, Advanced Closing", tasks: ["Launch client acquisition ad funnels", "Onboard helper or design content contractor", "Standardize standard operating procedures (SOPs)"], deadline: "Month 7", notes: "Shift mindset entirely from freelancer to business operator." },
            { id: 6, title: "Phase 6: Personal Brand", goals: "Establish authoritative industry profile online via structured platforms.", skills: "CapCut video styling, Content Frameworks", tasks: ["Plan systematic short-form video batch themes", "Publish weekly informative growth systems insights", "Launch specialized networking pipeline newsletter"], deadline: "Month 9", notes: "Inbound leads scale significantly when authority rises." },
            { id: 7, title: "Phase 7: Multiple Businesses", goals: "Diversify operational cashflows into parallel revenue streams.", skills: "System scaling, cross-market optimization", tasks: ["Identify adjacent market integration patterns", "Launch digital product or template ecosystem", "Automate tracking infrastructure dashboards"], deadline: "Month 12", notes: "Ensure primary business engine runs efficiently without manual monitoring." },
            { id: 8, title: "Phase 8: Empire", goals: "Achieve complete automated operations, equity systems, or exit options.", skills: "Macro-economics, organizational growth architecture", tasks: ["Secure long-term operations governance structure", "Deploy fully working sovereign AI systems tools", "Transition completely to chairman executive supervision"], deadline: "Long-term vision", notes: "The ultimate objective of the JV Digital Roadmap." }
        ];

        const initialSkillsData = [
            { id: "canva", name: "Canva", value: 40 },
            { id: "chatgpt", name: "ChatGPT Prompt Architecture", value: 65 },
            { id: "claude", name: "Claude Workflow Customization", value: 55 },
            { id: "capcut", name: "CapCut Video Production", value: 45 },
            { id: "content", name: "Content Strategy & Creation", value: 35 },
            { id: "smm", name: "Social Media Management", value: 50 },
            { id: "manychat", name: "ManyChat Automation", value: 25 },
            { id: "make", name: "Make.com Framework Syncs", value: 20 },
            { id: "meta", name: "Meta Paid Advertising", value: 15 },
            { id: "sales", name: "Sales & Client Negotiation", value: 30 }
        ];

        const businessQuotes = [
            "The best way to predict the future is to automate it.",
            "Your community determines your opportunities. Scale your vision.",
            "Grit means sticking with your long-term goals despite obstacles.",
            "Consistency transforms freelance operations into true business empires.",
            "Automation scales systems; true vision scales impact.",
            "Identify bottlenecks, install systematic procedures, step back."
        ];

        // --- 2. LOCAL STORAGE CONTROLLER STATE ENGINE ---
        let appState = {
            roadmap: JSON.parse(localStorage.getItem('jv_roadmap')) || initialRoadmapData,
            skills: JSON.parse(localStorage.getItem('jv_skills')) || initialSkillsData,
            tasks: JSON.parse(localStorage.getItem('jv_tasks')) || [],
            notes: JSON.parse(localStorage.getItem('jv_notes')) || []
        };

        function saveState() {
            localStorage.setItem('jv_roadmap', JSON.stringify(appState.roadmap));
            localStorage.setItem('jv_skills', JSON.stringify(appState.skills));
            localStorage.setItem('jv_tasks', JSON.stringify(appState.tasks));
            localStorage.setItem('jv_notes', JSON.stringify(appState.notes));
            updateMetrics();
        }

        // --- 3. UI SYSTEM DESIGN CONTROLLER ---
        function switchTab(tabId) {
            document.querySelectorAll('.tab-content').forEach(tab => {
                tab.classList.remove('active');
            });
            document.querySelectorAll('.nav-btn').forEach(btn => {
                btn.classList.remove('text-purple-500');
                btn.classList.add('text-zinc-500');
            });

            const currentTab = document.getElementById(`tab-${tabId}`);
            if (currentTab) {
                currentTab.classList.add('active');
            }
            
            const activeNavBtn = document.querySelector(`[data-tab="${tabId}"]`);
            if (activeNavBtn) {
                activeNavBtn.classList.remove('text-zinc-500');
                activeNavBtn.classList.add('text-purple-500');
            }
        }

        function setRandomQuote() {
            const randomIndex = Math.floor(Math.random() * businessQuotes.length);
            document.getElementById('motivational-quote').innerText = `"${businessQuotes[randomIndex]}"`;
        }

        // --- 4. ENGINE RENDERING LOGIC COMPONENTS ---
        
        // Calculate and Update Main Stats Dashboard
        function updateMetrics() {
            // Tasks completed total
            const doneTasksCount = appState.tasks.filter(t => t.completed).length;
            document.getElementById('stat-tasks').innerText = doneTasksCount;

            // Total notes stored
            document.getElementById('stat-notes').innerText = appState.notes.length;

            // Roadmap checklist items status metric
            let totalRoadmapTasks = 0;
            let completedRoadmapTasks = 0;
            appState.roadmap.forEach(phase => {
                if (phase.completedTasks && Array.isArray(phase.completedTasks)) {
                    completedRoadmapTasks += phase.completedTasks.length;
                }
                totalRoadmapTasks += phase.tasks.length;
            });

            const calcProgress = totalRoadmapTasks > 0 ? Math.round((completedRoadmapTasks / totalRoadmapTasks) * 100) : 0;
            document.getElementById('global-progress-txt').innerText = `${calcProgress}%`;
            document.getElementById('global-progress-bar').style.width = `${calcProgress}%`;
        }

        // Render Roadmap Accordions
        function renderRoadmap() {
            const container = document.getElementById('roadmap-accordion-container');
            container.innerHTML = '';

            appState.roadmap.forEach((phase) => {
                if (!phase.completedTasks) phase.completedTasks = [];
                
                const card = document.createElement('div');
                card.className = 'glass-card rounded-2xl overflow-hidden transition-all duration-300';
                
                // Header row
                const header = document.createElement('div');
                header.className = 'flex items-center justify-between p-4 cursor-pointer select-none border-b border-zinc-800/40 hover:bg-zinc-800/20';
                header.onclick = () => {
                    const body = document.getElementById(`phase-body-${phase.id}`);
                    const icon = document.getElementById(`phase-icon-${phase.id}`);
                    body.classList.toggle('hidden');
                    icon.style.transform = body.classList.contains('hidden') ? 'rotate(0deg)' : 'rotate(180deg)';
                };

                const titleGroup = document.createElement('div');
                titleGroup.className = 'flex items-center gap-2.5';
                
                const checkCount = phase.completedTasks.length;
                const totalCount = phase.tasks.length;
                const phaseDone = checkCount === totalCount;
                
                titleGroup.innerHTML = `
                    <div class="p-1.5 rounded-lg ${phaseDone ? 'bg-emerald-500/20 text-emerald-400' : 'bg-purple-500/10 text-purple-400'}">
                        <i data-lucide="${phaseDone ? 'check-circle-2' : 'circle'}" class="w-4 h-4"></i>
                    </div>
                    <div>
                        <h4 class="text-sm font-semibold text-white">${phase.title}</h4>
                        <p class="text-[10px] text-zinc-400 mt-0.5">${checkCount}/${totalCount} Completed · Deadline: <span class="text-zinc-300">${phase.deadline}</span></p>
                    </div>
                `;

                const controls = document.createElement('div');
                controls.className = 'text-zinc-500';
                controls.innerHTML = `<i data-lucide="chevron-down" id="phase-icon-${phase.id}" class="w-4 h-4 transition-transform duration-200"></i>`;
                
                header.appendChild(titleGroup);
                header.appendChild(controls);
                card.appendChild(header);

                // Body Section Accordion (Hidden by default)
                const body = document.createElement('div');
                body.id = `phase-body-${phase.id}`;
                body.className = 'p-4 space-y-4 hidden bg-zinc-950/40 border-t border-zinc-800/20 text-xs';
                
                // Detailed text info blocks
                body.innerHTML = `
                    <div>
                        <span class="text-[10px] uppercase tracking-wider text-purple-400 font-bold block mb-1">Target Goals</span>
                        <p class="text-zinc-300 font-medium leading-relaxed">${phase.goals}</p>
                    </div>
                    <div>
                        <span class="text-[10px] uppercase tracking-wider text-cyan-400 font-bold block mb-1">Skills Mastery Focal Points</span>
                        <p class="text-zinc-300 font-medium">${phase.skills}</p>
                    </div>
                `;

                // Sub-task Checklists
                const checklistContainer = document.createElement('div');
                checklistContainer.innerHTML = `<span class="text-[10px] uppercase tracking-wider text-pink-500 font-bold block mb-2">Milestone Checklist</span>`;
                
                const listWrapper = document.createElement('div');
                listWrapper.className = 'space-y-2';

                phase.tasks.forEach((task, index) => {
                    const isChecked = phase.completedTasks.includes(index);
                    const itemRow = document.createElement('div');
                    itemRow.className = 'flex items-center gap-2.5 bg-zinc-900/60 p-2.5 rounded-xl border border-zinc-800/60';
                    
                    const checkbox = document.createElement('input');
                    checkbox.type = 'checkbox';
                    checkbox.checked = isChecked;
                    checkbox.className = 'accent-purple-500 w-4 h-4 rounded border-zinc-700 bg-zinc-800 shrink-0';
                    checkbox.onchange = () => {
                        if (checkbox.checked) {
                            if (!phase.completedTasks.includes(index)) phase.completedTasks.push(index);
                        } else {
                            phase.completedTasks = phase.completedTasks.filter(idx => idx !== index);
                        }
                        saveState();
                        renderRoadmap();
                    };

                    const textSpan = document.createElement('span');
                    textSpan.className = `text-zinc-200 font-medium ${isChecked ? 'line-through text-zinc-500' : ''}`;
                    textSpan.innerText = task;

                    itemRow.appendChild(checkbox);
                    itemRow.appendChild(textSpan);
                    listWrapper.appendChild(itemRow);
                });

                checklistContainer.appendChild(listWrapper);
                body.appendChild(checklistContainer);

                // Notes dynamic internal section input field
                const notesBlock = document.createElement('div');
                notesBlock.innerHTML = `
                    <span class="text-[10px] uppercase tracking-wider text-zinc-400 font-bold block mb-1">Phase Execution Notes</span>
                    <textarea id="phase-notes-input-${phase.id}" rows="2" class="w-full bg-zinc-900/50 border border-zinc-700/60 rounded-xl px-2.5 py-2 text-xs text-zinc-300 focus:outline-none focus:border-purple-500" placeholder="Add custom notes specific to this phase...">${phase.notes || ''}</textarea>
                `;
                
                // Add blurring out text saved hook updates
                const textarea = notesBlock.querySelector('textarea');
                textarea.onblur = () => {
                    phase.notes = textarea.value;
                    saveState();
                };

                body.appendChild(notesBlock);
                card.appendChild(body);
                container.appendChild(card);
            });
            lucide.createIcons();
        }

        // Render Skill Matrix Trackers
        function renderSkills() {
            const container = document.getElementById('skills-container');
            container.innerHTML = '';

            appState.skills.forEach(skill => {
                const item = document.createElement('div');
                item.className = 'space-y-1.5';
                item.innerHTML = `
                    <div class="flex justify-between items-center text-xs">
                        <span class="font-semibold text-zinc-300">${skill.name}</span>
                        <div class="flex items-center gap-1.5">
                            <input type="number" value="${skill.value}" min="0" max="100" class="w-10 bg-transparent text-right font-bold text-purple-400 focus:outline-none" onchange="updateSkillVal('${skill.id}', this.value)">
                            <span class="text-[10px] text-zinc-500 font-bold">%</span>
                        </div>
                    </div>
                    <div class="w-full bg-zinc-800/60 h-2 rounded-full overflow-hidden border border-zinc-700/30">
                        <div class="bg-gradient-to-r from-purple-500 to-pink-500 h-full transition-all duration-300" style="width: ${skill.value}%"></div>
                    </div>
                `;
                container.appendChild(item);
            });
        }

        function updateSkillVal(skillId, val) {
            let numericVal = parseInt(val) || 0;
            if (numericVal > 100) numericVal = 100;
            if (numericVal < 0) numericVal = 0;
            
            const item = appState.skills.find(s => s.id === skillId);
            if (item) {
                item.value = numericVal;
                saveState();
                renderSkills();
            }
        }

        // Render General Quick Tasks Manager
        function renderTasks() {
            const list = document.getElementById('todo-list');
            list.innerHTML = '';

            appState.tasks.forEach((task, index) => {
                const row = document.createElement('div');
                row.className = 'flex items-center justify-between glass-card p-3 rounded-xl gap-2 border-zinc-800/60';
                
                const itemLeft = document.createElement('div');
                itemLeft.className = 'flex items-center gap-2.5';
                
                const check = document.createElement('input');
                check.type = 'checkbox';
                check.checked = task.completed;
                check.className = 'accent-purple-500 w-4 h-4 shrink-0 rounded';
                check.onchange = () => {
                    task.completed = check.checked;
                    saveState();
                    renderTasks();
                };

                const text = document.createElement('span');
                text.className = `text-xs font-medium text-zinc-200 ${task.completed ? 'line-through text-zinc-500' : ''}`;
                text.innerText = task.text;

                itemLeft.appendChild(check);
                itemLeft.appendChild(text);

                const deleteBtn = document.createElement('button');
                deleteBtn.className = 'text-zinc-500 hover:text-pink-500 p-1 transition-colors';
                deleteBtn.innerHTML = `<i data-lucide="trash-2" class="w-3.5 h-3.5"></i>`;
                deleteBtn.onclick = () => {
                    appState.tasks.splice(index, 1);
                    saveState();
                    renderTasks();
                };

                row.appendChild(itemLeft);
                row.appendChild(deleteBtn);
                list.appendChild(row);
            });
            lucide.createIcons();
        }

        // Handle Add Task Submission Form
        document.getElementById('todo-form').onsubmit = (e) => {
            e.preventDefault();
            const input = document.getElementById('todo-input');
            const txt = input.value.trim();
            if (txt) {
                appState.tasks.unshift({ text: txt, completed: false });
                input.value = '';
                saveState();
                renderTasks();
            }
        };

        // Render Personal Idea Entries & Notes Layout
        function renderNotes() {
            const container = document.getElementById('notes-grid');
            container.innerHTML = '';

            if (appState.notes.length === 0) {
                container.innerHTML = `<p class="text-zinc-500 text-xs italic text-center py-4">No strategic notes saved yet.</p>`;
                return;
            }

            appState.notes.forEach((note, index) => {
                const card = document.createElement('div');
                card.className = 'glass-card rounded-xl p-4 space-y-2 relative';
                card.innerHTML = `
                    <div class="flex justify-between items-start pr-6">
                        <h4 class="text-xs font-bold text-white tracking-wide uppercase">${note.title || 'Untitled Entry'}</h4>
                        <span class="text-[9px] text-zinc-500 font-medium">${note.date}</span>
                    </div>
                    <p class="text-xs text-zinc-300 font-medium whitespace-pre-wrap leading-relaxed">${note.content}</p>
                    <button class="absolute top-2 right-2 text-zinc-600 hover:text-pink-400 transition-colors p-1" onclick="deleteNote(${index})">
                        <i data-lucide="x" class="w-3.5 h-3.5"></i>
                    </button>
                `;
                container.appendChild(card);
            });
            lucide.createIcons();
        }

        document.getElementById('save-note-btn').onclick = () => {
            const titleInp = document.getElementById('note-title');
            const contentInp = document.getElementById('note-content');
            
            const title = titleInp.value.trim();
            const content = contentInp.value.trim();
            
            if (!content) return; // Prevent saving completely blank note entries

            const dateStr = new Date().toLocaleDateString('en-US', { month: 'short', day: 'numeric', year: 'numeric' });
            
            appState.notes.unshift({ title, content, date: dateStr });
            titleInp.value = '';
            contentInp.value = '';
            
            saveState();
            renderNotes();
        };

        function deleteNote(index) {
            appState.notes.splice(index, 1);
            saveState();
            renderNotes();
        }

        // --- 5. INITIALIZATION SEQUENCE ---
        window.onload = () => {
            lucide.createIcons();
            setRandomQuote();
            updateMetrics();
            renderRoadmap();
            renderSkills();
            renderTasks();
            renderNotes();
        };

        // --- 6. OFFLINE CAPABILITY & PROGRESSIVE WEB APP (PWA) SERVICE WORKER EMBED ---
        if ('serviceWorker' in navigator) {
            // Encode Service Worker code directly as an inline data URL data blob to maintain the complete single file package structure safely
            const swCode = `
                const CACHE_NAME = 'jv-digital-v1';
                const ASSETS = [
                    './',
                    'index.html',
                    'https://cdn.jsdelivr.net/npm/@tailwindcss/browser@4',
                    'https://unpkg.com/lucide@latest'
                ];
                self.addEventListener('install', e => {
                    e.waitUntil(caches.open(CACHE_NAME).then(cache => cache.addAll(ASSETS)));
                });
                self.addEventListener('fetch', e => {
                    e.respondWith(caches.match(e.request).then(res => res || fetch(e.request)));
                });
            `;
            const blob = new Blob([swCode], { type: 'application/javascript' });
            const workerUrl = URL.createObjectURL(blob);
            
            navigator.serviceWorker.register(workerUrl)
                .then(() => console.log("PWA Engine Activated Successfully"))
                .catch(err => console.log("SW Engine failed offline sync configuration: ", err));
        }

        // Install app display banner logic trigger handling hook
        let deferredPrompt;
        window.addEventListener('beforeinstallprompt', (e) => {
            e.preventDefault();
            deferredPrompt = e;
            document.getElementById('pwa-install-container').classList.remove('hidden');
        });

        document.getElementById('btn-install').addEventListener('click', async () => {
            if (deferredPrompt) {
                deferredPrompt.prompt();
                const { outcome } = await deferredPrompt.userChoice;
                if (outcome === 'accepted') {
                    document.getElementById('pwa-install-container').classList.add('hidden');
                }
                deferredPrompt = null;
            }
        });
    </script>
</body>
</html>
 Empire-dashboard
