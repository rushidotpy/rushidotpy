## Hi, I'm Rushi
I am a recent Computer Science graduate student at UNT. <br/>
I architect and deploy cutting-edge data science and AI solutions. <br/>
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>AI/LLM Portfolio Dashboard</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            background: linear-gradient(135deg, #1a1a2e 0%, #16213e 50%, #0f3460 100%);
            color: #e0e6ed;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            min-height: 100vh;
            padding: 20px;
        }
        
        .container {
            max-width: 1400px;
            margin: 0 auto;
        }
        
        .header {
            text-align: center;
            margin-bottom: 40px;
        }
        
        .header h1 {
            font-size: 2.5rem;
            background: linear-gradient(45deg, #4facfe, #00f2fe);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            margin-bottom: 10px;
        }
        
        .header p {
            font-size: 1.2rem;
            color: #8892b0;
        }
        
        .dashboard-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
            gap: 25px;
            margin-bottom: 30px;
        }
        
        .card {
            background: rgba(20, 25, 50, 0.8);
            border: 1px solid rgba(100, 255, 218, 0.1);
            border-radius: 15px;
            padding: 25px;
            backdrop-filter: blur(10px);
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
        }
        
        .card::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            height: 3px;
            background: linear-gradient(90deg, #4facfe, #00f2fe);
            opacity: 0;
            transition: opacity 0.3s ease;
        }
        
        .card:hover {
            transform: translateY(-5px);
            border-color: rgba(100, 255, 218, 0.3);
            box-shadow: 0 20px 40px rgba(0, 242, 254, 0.1);
        }
        
        .card:hover::before {
            opacity: 1;
        }
        
        .card-header {
            display: flex;
            align-items: center;
            margin-bottom: 20px;
        }
        
        .card-icon {
            width: 40px;
            height: 40px;
            margin-right: 15px;
            border-radius: 8px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.5rem;
        }
        
        .card-title {
            font-size: 1.3rem;
            font-weight: 600;
            color: #ccd6f6;
        }
        
        .stats-grid {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 15px;
        }
        
        .stat-item {
            background: rgba(100, 255, 218, 0.05);
            padding: 15px;
            border-radius: 8px;
            border-left: 3px solid #64ffda;
        }
        
        .stat-number {
            font-size: 1.8rem;
            font-weight: bold;
            color: #64ffda;
            display: block;
        }
        
        .stat-label {
            font-size: 0.9rem;
            color: #8892b0;
            margin-top: 5px;
        }
        
        .skill-bar {
            margin-bottom: 15px;
        }
        
        .skill-name {
            font-size: 0.95rem;
            margin-bottom: 8px;
            color: #ccd6f6;
        }
        
        .progress-bar {
            background: rgba(100, 255, 218, 0.1);
            height: 8px;
            border-radius: 4px;
            overflow: hidden;
        }
        
        .progress-fill {
            height: 100%;
            background: linear-gradient(90deg, #4facfe, #00f2fe);
            border-radius: 4px;
            transition: width 0.8s ease;
        }
        
        .project-item {
            background: rgba(100, 255, 218, 0.05);
            padding: 15px;
            border-radius: 8px;
            margin-bottom: 15px;
            border-left: 3px solid #4facfe;
        }
        
        .project-title {
            font-size: 1.1rem;
            color: #ccd6f6;
            margin-bottom: 5px;
        }
        
        .project-desc {
            font-size: 0.9rem;
            color: #8892b0;
            margin-bottom: 8px;
        }
        
        .project-tech {
            display: flex;
            flex-wrap: wrap;
            gap: 5px;
        }
        
        .tech-tag {
            background: rgba(79, 172, 254, 0.2);
            color: #4facfe;
            padding: 3px 8px;
            border-radius: 12px;
            font-size: 0.8rem;
        }
        
        .learning-path {
            display: flex;
            flex-direction: column;
            gap: 10px;
        }
        
        .path-item {
            display: flex;
            align-items: center;
            padding: 10px;
            background: rgba(100, 255, 218, 0.05);
            border-radius: 8px;
            border-left: 3px solid;
        }
        
        .path-item.completed { border-left-color: #64ffda; }
        .path-item.in-progress { border-left-color: #ffd700; }
        .path-item.planned { border-left-color: #8892b0; }
        
        .path-status {
            width: 12px;
            height: 12px;
            border-radius: 50%;
            margin-right: 12px;
        }
        
        .path-status.completed { background: #64ffda; }
        .path-status.in-progress { background: #ffd700; }
        .path-status.planned { background: #8892b0; }
        
        .github-activity {
            display: grid;
            grid-template-columns: repeat(7, 1fr);
            gap: 3px;
            margin-top: 15px;
        }
        
        .activity-day {
            width: 12px;
            height: 12px;
            border-radius: 2px;
            background: rgba(100, 255, 218, 0.1);
        }
        
        .activity-day.level-1 { background: rgba(100, 255, 218, 0.3); }
        .activity-day.level-2 { background: rgba(100, 255, 218, 0.5); }
        .activity-day.level-3 { background: rgba(100, 255, 218, 0.7); }
        .activity-day.level-4 { background: #64ffda; }
        
        @keyframes fadeInUp {
            from {
                opacity: 0;
                transform: translateY(30px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }
        
        .card {
            animation: fadeInUp 0.6s ease forwards;
        }
        
        .card:nth-child(2) { animation-delay: 0.1s; }
        .card:nth-child(3) { animation-delay: 0.2s; }
        .card:nth-child(4) { animation-delay: 0.3s; }
        .card:nth-child(5) { animation-delay: 0.4s; }
        .card:nth-child(6) { animation-delay: 0.5s; }
    </style>
</head>
<body>
    <div class="container">
        <div class="header">
            <h1>AI/LLM Portfolio Dashboard</h1>
            <p>Exploring the Future of Artificial Intelligence & Large Language Models</p>
        </div>
        
        <div class="dashboard-grid">
            <!-- Learning Progress -->
            <div class="card">
                <div class="card-header">
                    <div class="card-icon" style="background: linear-gradient(135deg, #667eea, #764ba2);">🧠</div>
                    <div class="card-title">AI Learning Journey</div>
                </div>
                <div class="learning-path">
                    <div class="path-item completed">
                        <div class="path-status completed"></div>
                        <div>
                            <div style="font-size: 0.95rem; color: #ccd6f6;">Machine Learning Fundamentals</div>
                            <div style="font-size: 0.8rem; color: #8892b0;">Completed</div>
                        </div>
                    </div>
                    <div class="path-item in-progress">
                        <div class="path-status in-progress"></div>
                        <div>
                            <div style="font-size: 0.95rem; color: #ccd6f6;">LangChain & LangGraph</div>
                            <div style="font-size: 0.8rem; color: #ffd700;">In Progress</div>
                        </div>
                    </div>
                    <div class="path-item in-progress">
                        <div class="path-status in-progress"></div>
                        <div>
                            <div style="font-size: 0.95rem; color: #ccd6f6;">RAG Systems</div>
                            <div style="font-size: 0.8rem; color: #ffd700;">In Progress</div>
                        </div>
                    </div>
                    <div class="path-item planned">
                        <div class="path-status planned"></div>
                        <div>
                            <div style="font-size: 0.95rem; color: #ccd6f6;">LLM Fine-tuning</div>
                            <div style="font-size: 0.8rem; color: #8892b0;">Planned</div>
                        </div>
                    </div>
                    <div class="path-item planned">
                        <div class="path-status planned"></div>
                        <div>
                            <div style="font-size: 0.95rem; color: #ccd6f6;">Agentic AI Systems</div>
                            <div style="font-size: 0.8rem; color: #8892b0;">Planned</div>
                        </div>
                    </div>
                </div>
            </div>
            
            <!-- Technical Skills -->
            <div class="card">
                <div class="card-header">
                    <div class="card-icon" style="background: linear-gradient(135deg, #f093fb, #f5576c);">⚡</div>
                    <div class="card-title">Technical Skills</div>
                </div>
                <div class="skill-bar">
                    <div class="skill-name">Python & ML Libraries</div>
                    <div class="progress-bar">
                        <div class="progress-fill" style="width: 85%;"></div>
                    </div>
                </div>
                <div class="skill-bar">
                    <div class="skill-name">LangChain Framework</div>
                    <div class="progress-bar">
                        <div class="progress-fill" style="width: 60%;"></div>
                    </div>
                </div>
                <div class="skill-bar">
                    <div class="skill-name">RAG Implementation</div>
                    <div class="progress-bar">
                        <div class="progress-fill" style="width: 45%;"></div>
                    </div>
                </div>
                <div class="skill-bar">
                    <div class="skill-name">Vector Databases</div>
                    <div class="progress-bar">
                        <div class="progress-fill" style="width: 40%;"></div>
                    </div>
                </div>
                <div class="skill-bar">
                    <div class="skill-name">LLM APIs (OpenAI, Anthropic)</div>
                    <div class="progress-bar">
                        <div class="progress-fill" style="width: 70%;"></div>
                    </div>
                </div>
            </div>
            
            <!-- Project Portfolio -->
            <div class="card">
                <div class="card-header">
                    <div class="card-icon" style="background: linear-gradient(135deg, #4facfe, #00f2fe);">🚀</div>
                    <div class="card-title">AI Projects</div>
                </div>
                <div class="project-item">
                    <div class="project-title">Document Q&A RAG System</div>
                    <div class="project-desc">RAG system for document analysis with vector search</div>
                    <div class="project-tech">
                        <span class="tech-tag">LangChain</span>
                        <span class="tech-tag">ChromaDB</span>
                        <span class="tech-tag">OpenAI</span>
                    </div>
                </div>
                <div class="project-item">
                    <div class="project-title">Multi-Agent Chatbot</div>
                    <div class="project-desc">Conversational AI with multiple specialized agents</div>
                    <div class="project-tech">
                        <span class="tech-tag">LangGraph</span>
                        <span class="tech-tag">Streamlit</span>
                        <span class="tech-tag">Python</span>
                    </div>
                </div>
                <div class="project-item">
                    <div class="project-title">Knowledge Graph RAG</div>
                    <div class="project-desc">Graph-based retrieval system for complex queries</div>
                    <div class="project-tech">
                        <span class="tech-tag">Neo4j</span>
                        <span class="tech-tag">GraphRAG</span>
                        <span class="tech-tag">LLM</span>
                    </div>
                </div>
            </div>
            
            <!-- Learning Stats -->
            <div class="card">
                <div class="card-header">
                    <div class="card-icon" style="background: linear-gradient(135deg, #fa709a, #fee140);">📊</div>
                    <div class="card-title">Learning Statistics</div>
                </div>
                <div class="stats-grid">
                    <div class="stat-item">
                        <span class="stat-number">12</span>
                        <div class="stat-label">AI Projects Built</div>
                    </div>
                    <div class="stat-item">
                        <span class="stat-number">5</span>
                        <div class="stat-label">RAG Systems</div>
                    </div>
                    <div class="stat-item">
                        <span class="stat-number">8</span>
                        <div class="stat-label">LLM Integrations</div>
                    </div>
                    <div class="stat-item">
                        <span class="stat-number">15</span>
                        <div class="stat-label">Days Learning Streak</div>
                    </div>
                </div>
            </div>
            
            <!-- Research Focus -->
            <div class="card">
                <div class="card-header">
                    <div class="card-icon" style="background: linear-gradient(135deg, #a8edea, #fed6e3);">🔬</div>
                    <div class="card-title">Research Areas</div>
                </div>
                <div class="project-item">
                    <div class="project-title">Retrieval-Augmented Generation</div>
                    <div class="project-desc">Exploring advanced RAG architectures and optimization techniques</div>
                </div>
                <div class="project-item">
                    <div class="project-title">Agentic AI Systems</div>
                    <div class="project-desc">Building autonomous AI agents with planning and reasoning capabilities</div>
                </div>
                <div class="project-item">
                    <div class="project-title">LLM Architecture Analysis</div>
                    <div class="project-desc">Deep dive into transformer architectures and attention mechanisms</div>
                </div>
            </div>
            
            <!-- GitHub Activity -->
            <div class="card">
                <div class="card-header">
                    <div class="card-icon" style="background: linear-gradient(135deg, #667eea, #764ba2);">📈</div>
                    <div class="card-title">Coding Activity</div>
                </div>
                <div class="stats-grid">
                    <div class="stat-item">
                        <span class="stat-number">45</span>
                        <div class="stat-label">Commits This Month</div>
                    </div>
                    <div class="stat-item">
                        <span class="stat-number">7</span>
                        <div class="stat-label">Active Repositories</div>
                    </div>
                </div>
                <div style="margin-top: 15px; font-size: 0.9rem; color: #8892b0; margin-bottom: 10px;">Recent Activity</div>
                <div class="github-activity">
                    <!-- Activity visualization -->
                    <div class="activity-day level-1"></div>
                    <div class="activity-day level-2"></div>
                    <div class="activity-day level-0"></div>
                    <div class="activity-day level-3"></div>
                    <div class="activity-day level-2"></div>
                    <div class="activity-day level-4"></div>
                    <div class="activity-day level-1"></div>
                    <div class="activity-day level-2"></div>
                    <div class="activity-day level-1"></div>
                    <div class="activity-day level-0"></div>
                    <div class="activity-day level-3"></div>
                    <div class="activity-day level-2"></div>
                    <div class="activity-day level-1"></div>
                    <div class="activity-day level-4"></div>
                    <div class="activity-day level-3"></div>
                    <div class="activity-day level-2"></div>
                    <div class="activity-day level-1"></div>
                    <div class="activity-day level-2"></div>
                    <div class="activity-day level-0"></div>
                    <div class="activity-day level-1"></div>
                    <div class="activity-day level-3"></div>
                </div>
            </div>
        </div>
    </div>
</body>
</html>
