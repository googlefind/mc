<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Electric Fault Line Transmission Monitor</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            padding: 20px;
        }

        .container {
            max-width: 1400px;
            margin: 0 auto;
        }

        header {
            background: white;
            padding: 30px;
            border-radius: 15px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.2);
            margin-bottom: 30px;
            text-align: center;
        }

        h1 {
            color: #333;
            font-size: 2.5em;
            margin-bottom: 10px;
        }

        .subtitle {
            color: #666;
            font-size: 1.1em;
        }

        .main-content {
            display: grid;
            grid-template-columns: 2fr 1fr;
            gap: 30px;
            margin-bottom: 30px;
        }

        .monitor-section, .complaint-section {
            background: white;
            padding: 30px;
            border-radius: 15px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.2);
        }

        .section-title {
            color: #667eea;
            font-size: 1.8em;
            margin-bottom: 20px;
            padding-bottom: 10px;
            border-bottom: 3px solid #667eea;
        }

        .iframe-container {
            position: relative;
            width: 100%;
            height: 600px;
            border: 3px solid #667eea;
            border-radius: 10px;
            overflow: hidden;
            background: #f5f5f5;
        }

        iframe {
            width: 100%;
            height: 100%;
            border: none;
        }

        .connection-status {
            margin-top: 15px;
            padding: 15px;
            background: #e8f5e9;
            border-left: 4px solid #4caf50;
            border-radius: 5px;
        }

        .status-indicator {
            display: inline-block;
            width: 12px;
            height: 12px;
            background: #4caf50;
            border-radius: 50%;
            margin-right: 10px;
            animation: pulse 2s infinite;
        }

        @keyframes pulse {
            0%, 100% { opacity: 1; }
            50% { opacity: 0.5; }
        }

        .form-group {
            margin-bottom: 20px;
        }

        label {
            display: block;
            color: #333;
            font-weight: 600;
            margin-bottom: 8px;
        }

        input, textarea, select {
            width: 100%;
            padding: 12px;
            border: 2px solid #ddd;
            border-radius: 8px;
            font-size: 1em;
            transition: all 0.3s;
        }

        input:focus, textarea:focus, select:focus {
            outline: none;
            border-color: #667eea;
            box-shadow: 0 0 0 3px rgba(102, 126, 234, 0.1);
        }

        textarea {
            resize: vertical;
            min-height: 120px;
        }

        .submit-btn {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            padding: 15px 40px;
            border: none;
            border-radius: 8px;
            font-size: 1.1em;
            font-weight: 600;
            cursor: pointer;
            width: 100%;
            transition: transform 0.2s, box-shadow 0.2s;
        }

        .submit-btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 5px 20px rgba(102, 126, 234, 0.4);
        }

        .submit-btn:active {
            transform: translateY(0);
        }

        .success-message {
            display: none;
            background: #4caf50;
            color: white;
            padding: 15px;
            border-radius: 8px;
            margin-top: 15px;
            text-align: center;
        }

        .info-cards {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 20px;
            margin-bottom: 30px;
        }

        .info-card {
            background: white;
            padding: 25px;
            border-radius: 15px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.2);
            text-align: center;
        }

        .info-card h3 {
            color: #667eea;
            margin-bottom: 10px;
        }

        .info-card p {
            color: #666;
            font-size: 0.95em;
        }

        @media (max-width: 968px) {
            .main-content {
                grid-template-columns: 1fr;
            }

            h1 {
                font-size: 2em;
            }

            .iframe-container {
                height: 500px;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <h1>⚡ Electric Fault Line Transmission Monitor</h1>
            <p class="subtitle">Real-Time Monitoring & Fault Detection System</p>
        </header>

        <div class="info-cards">
            <div class="info-card">
                <h3>🔍 Real-Time Monitoring</h3>
                <p>Live transmission line status and fault detection</p>
            </div>
            <div class="info-card">
                <h3>🚨 Instant Alerts</h3>
                <p>Immediate notification of electrical faults</p>
            </div>
            <div class="info-card">
                <h3>📊 Data Analytics</h3>
                <p>Comprehensive fault analysis and reporting</p>
            </div>
        </div>

        <div class="main-content">
            <div class="monitor-section">
                <h2 class="section-title">Live Transmission Monitor</h2>
                <div class="iframe-container">
                    <iframe src="http://10.158.232.148" title="ESP32 Fault Monitor"></iframe>
                </div>
                <div class="connection-status">
                    <span class="status-indicator"></span>
                    <strong>System Status:</strong> Connected to ESP32 Server (10.158.232.148)
                </div>
            </div>

            <div class="complaint-section">
                <h2 class="section-title">Report Fault</h2>
                <form id="complaintForm">
                    <div class="form-group">
                        <label for="name">Your Name *</label>
                        <input type="text" id="name" name="name" required>
                    </div>

                    <div class="form-group">
                        <label for="contact">Contact Number *</label>
                        <input type="tel" id="contact" name="contact" required>
                    </div>

                    <div class="form-group">
                        <label for="email">Email Address</label>
                        <input type="email" id="email" name="email">
                    </div>

                    <div class="form-group">
                        <label for="location">Fault Location *</label>
                        <input type="text" id="location" name="location" placeholder="e.g., Street name, Area" required>
                    </div>

                    <div class="form-group">
                        <label for="faultType">Fault Type *</label>
                        <select id="faultType" name="faultType" required>
                            <option value="">Select Fault Type</option>
                            <option value="power_outage">Power Outage</option>
                            <option value="voltage_fluctuation">Voltage Fluctuation</option>
                            <option value="line_damage">Transmission Line Damage</option>
                            <option value="sparking">Electrical Sparking</option>
                            <option value="transformer_issue">Transformer Issue</option>
                            <option value="other">Other</option>
                        </select>
                    </div>

                    <div class="form-group">
                        <label for="description">Fault Description *</label>
                        <textarea id="description" name="description" placeholder="Please describe the fault in detail..." required></textarea>
                    </div>

                    <button type="submit" class="submit-btn">Submit Complaint</button>
                    <div class="success-message" id="successMessage">
                        ✓ Complaint submitted successfully! Reference ID: <span id="refId"></span>
                    </div>
                </form>
            </div>
        </div>
    </div>

    <script>
        document.getElementById('complaintForm').addEventListener('submit', function(e) {
            e.preventDefault();
            
            // Generate reference ID
            const refId = 'FLT' + Date.now().toString().slice(-8);
            
            // Get form data
            const formData = {
                refId: refId,
                name: document.getElementById('name').value,
                contact: document.getElementById('contact').value,
                email: document.getElementById('email').value,
                location: document.getElementById('location').value,
                faultType: document.getElementById('faultType').value,
                description: document.getElementById('description').value,
                timestamp: new Date().toLocaleString()
            };
            
            // Store in memory (in a real application, this would be sent to a server)
            console.log('Complaint Data:', formData);
            
            // Show success message
            document.getElementById('refId').textContent = refId;
            document.getElementById('successMessage').style.display = 'block';
            
            // Reset form
            this.reset();
            
            // Hide success message after 5 seconds
            setTimeout(() => {
                document.getElementById('successMessage').style.display = 'none';
            }, 5000);
        });
    </script>
</body>
</html>