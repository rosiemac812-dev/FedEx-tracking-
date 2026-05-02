<!DOCTYPE html>
<html lang="en">
<head>
   <meta charset="UTF-8">
   <meta name="viewport" content="width=device-width, initial-scale=1.0">
   <title>FedEx | Track Shipment</title>
   <style>
       * {
           margin: 0;
           padding: 0;
           box-sizing: border-box;
       }

       body {
           font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
           background-color: #f5f5f5;
           color: #333;
           min-height: 100vh;
       }

       /* FedEx Header */
       .header {
           background: linear-gradient(135deg, #4D148C 0%, #6B21A8 100%);
           color: white;
           padding: 15px 0;
           box-shadow: 0 2px 10px rgba(0,0,0,0.1);
           position: sticky;
           top: 0;
           z-index: 100;
       }

       .header-content {
           max-width: 1200px;
           margin: 0 auto;
           padding: 0 20px;
           display: flex;
           justify-content: space-between;
           align-items: center;
       }

       .logo {
           font-size: 28px;
           font-weight: bold;
           letter-spacing: -1px;
           cursor: pointer;
       }

       .logo span {
           color: #FF6600;
       }

       .nav-links {
           display: flex;
           gap: 30px;
       }

       .nav-links a {
           color: white;
           text-decoration: none;
           font-size: 14px;
           font-weight: 500;
           transition: opacity 0.3s;
           cursor: pointer;
       }

       .nav-links a:hover {
           opacity: 0.8;
       }

       /* Main Container */
       .container {
           max-width: 1000px;
           margin: 40px auto;
           padding: 0 20px;
       }

       /* Tracking Input Section - Landing Page */
       .tracking-landing {
           background: white;
           padding: 60px 40px;
           border-radius: 8px;
           box-shadow: 0 2px 15px rgba(0,0,0,0.08);
           text-align: center;
           max-width: 700px;
           margin: 60px auto;
       }

       .tracking-landing h1 {
           color: #4D148C;
           font-size: 32px;
           margin-bottom: 10px;
       }

       .tracking-landing p {
           color: #666;
           margin-bottom: 30px;
           font-size: 16px;
       }

       .tracking-input-group {
           display: flex;
           gap: 10px;
           margin-top: 15px;
           max-width: 600px;
           margin-left: auto;
           margin-right: auto;
       }

       .tracking-input {
           flex: 1;
           padding: 15px 20px;
           border: 2px solid #ddd;
           border-radius: 4px;
           font-size: 18px;
           transition: border-color 0.3s;
           font-family: 'Courier New', monospace;
           text-transform: uppercase;
       }

       .tracking-input:focus {
           outline: none;
           border-color: #4D148C;
       }

       .track-btn {
           background: #FF6600;
           color: white;
           border: none;
           padding: 15px 40px;
           border-radius: 4px;
           font-size: 16px;
           font-weight: bold;
           cursor: pointer;
           transition: background 0.3s;
       }

       .track-btn:hover {
           background: #e55a00;
       }

       .track-btn:disabled {
           background: #ccc;
           cursor: not-allowed;
       }

       .error-message {
           color: #d32f2f;
           margin-top: 15px;
           padding: 12px;
           background: #ffebee;
           border-radius: 4px;
           display: none;
           font-size: 14px;
           border-left: 4px solid #d32f2f;
       }

       .error-message.show {
           display: block;
           animation: shake 0.5s;
       }

       @keyframes shake {
           0%, 100% { transform: translateX(0); }
           25% { transform: translateX(-10px); }
           75% { transform: translateX(10px); }
       }

       /* Shipment Status Page - Hidden by default */
       .status-page {
           display: none;
       }

       .status-page.active {
           display: block;
           animation: fadeIn 0.5s;
       }

       @keyframes fadeIn {
           from { opacity: 0; transform: translateY(20px); }
           to { opacity: 1; transform: translateY(0); }
       }

       /* Status Card */
       .status-card {
           background: white;
           border-radius: 8px;
           box-shadow: 0 2px 15px rgba(0,0,0,0.08);
           overflow: hidden;
           margin-bottom: 30px;
       }

       .status-header {
           background: linear-gradient(135deg, #4D148C 0%, #6B21A8 100%);
           color: white;
           padding: 25px 30px;
       }

       .status-badge {
           display: inline-block;
           background: #FF6600;
           color: white;
           padding: 6px 16px;
           border-radius: 20px;
           font-size: 12px;
           font-weight: bold;
           text-transform: uppercase;
           letter-spacing: 0.5px;
           margin-bottom: 10px;
       }

       .status-title {
           font-size: 24px;
           font-weight: bold;
           margin-bottom: 5px;
       }

       .tracking-number-display {
           font-size: 14px;
           opacity: 0.9;
           font-family: 'Courier New', monospace;
       }

       /* Progress Bar */
       .progress-section {
           padding: 30px;
           border-bottom: 1px solid #eee;
       }

       .progress-bar {
           display: flex;
           justify-content: space-between;
           position: relative;
           margin: 20px 0;
       }

       .progress-line {
           position: absolute;
           top: 15px;
           left: 0;
           right: 0;
           height: 4px;
           background: #e0e0e0;
           z-index: 1;
       }

       .progress-line-fill {
           height: 100%;
           background: linear-gradient(90deg, #4D148C, #FF6600);
           width: 35%;
           transition: width 1s ease;
       }

       .progress-step {
           position: relative;
           z-index: 2;
           text-align: center;
           flex: 1;
       }

       .step-circle {
           width: 34px;
           height: 34px;
           border-radius: 50%;
           background: white;
           border: 3px solid #ddd;
           margin: 0 auto 8px;
           display: flex;
           align-items: center;
           justify-content: center;
           font-weight: bold;
           font-size: 14px;
           transition: all 0.3s;
       }

       .progress-step.completed .step-circle {
           background: #4D148C;
           border-color: #4D148C;
           color: white;
       }

       .progress-step.active .step-circle {
           background: #FF6600;
           border-color: #FF6600;
           color: white;
           animation: pulse 2s infinite;
       }

       @keyframes pulse {
           0%, 100% { transform: scale(1); }
           50% { transform: scale(1.1); }
       }

       .step-label {
           font-size: 12px;
           color: #666;
           font-weight: 500;
       }

       .progress-step.completed .step-label,
       .progress-step.active .step-label {
           color: #333;
           font-weight: bold;
       }

       /* Route Map */
       .route-section {
           padding: 30px;
           border-bottom: 1px solid #eee;
       }

       .section-title {
           font-size: 18px;
           font-weight: bold;
           color: #4D148C;
           margin-bottom: 20px;
           display: flex;
           align-items: center;
           gap: 10px;
       }

       .route-container {
           background: linear-gradient(135deg, #f8f9fa 0%, #e9ecef 100%);
           border-radius: 12px;
           padding: 30px;
           position: relative;
           overflow: hidden;
       }

       .route-visual {
           display: flex;
           align-items: center;
           justify-content: space-between;
           position: relative;
           z-index: 2;
       }

       .location-box {
           text-align: center;
           background: white;
           padding: 20px;
           border-radius: 10px;
           box-shadow: 0 4px 15px rgba(0,0,0,0.1);
           min-width: 180px;
       }

       .location-icon {
           font-size: 36px;
           margin-bottom: 10px;
       }

       .location-city {
           font-size: 18px;
           font-weight: bold;
           color: #4D148C;
           margin-bottom: 5px;
       }

       .location-country {
           font-size: 14px;
           color: #666;
       }

       .flight-path {
           flex: 1;
           margin: 0 20px;
           position: relative;
           height: 60px;
           display: flex;
           align-items: center;
           justify-content: center;
       }

       .flight-line {
           width: 100%;
           height: 3px;
           background: #e0e0e0;
           position: relative;
           border-radius: 2px;
       }

       .plane-icon {
           position: absolute;
           top: 50%;
           transform: translateY(-50%);
           font-size: 30px;
           left: 15%;
           filter: grayscale(100%);
           opacity: 0.5;
       }

       .flight-info {
           position: absolute;
           bottom: -25px;
           left: 50%;
           transform: translateX(-50%);
           font-size: 12px;
           color: #999;
           font-weight: bold;
           white-space: nowrap;
       }

       .status-pending-box {
           margin-top: 20px;
           padding: 20px;
           background: #fff3e0;
           border-radius: 8px;
           border-left: 4px solid #FF6600;
           text-align: center;
       }

       .status-pending-box .pending-title {
           font-size: 18px;
           font-weight: bold;
           color: #FF6600;
           margin-bottom: 8px;
       }

       .status-pending-box .pending-desc {
           font-size: 14px;
           color: #666;
       }

       /* Shipment Details */
       .details-section {
           padding: 30px;
           display: grid;
           grid-template-columns: 1fr 1fr;
           gap: 30px;
       }

       .detail-card {
           background: #f8f9fa;
           padding: 25px;
           border-radius: 8px;
           border-left: 4px solid #4D148C;
       }

       .detail-card.receiver {
           border-left-color: #FF6600;
       }

       .detail-label {
           font-size: 12px;
           text-transform: uppercase;
           letter-spacing: 0.5px;
           color: #666;
           margin-bottom: 8px;
           font-weight: 600;
       }

       .detail-value {
           font-size: 16px;
           color: #333;
           line-height: 1.6;
       }

       .detail-value.name {
           font-size: 20px;
           font-weight: bold;
           color: #4D148C;
       }

       .detail-value.highlight {
           color: #FF6600;
           font-weight: bold;
       }

       /* Tracking History */
       .history-section {
           padding: 30px;
       }

       .timeline {
           position: relative;
           padding-left: 30px;
       }

       .timeline::before {
           content: '';
           position: absolute;
           left: 8px;
           top: 0;
           bottom: 0;
           width: 2px;
           background: #e0e0e0;
       }

       .timeline-item {
           position: relative;
           margin-bottom: 25px;
           padding-bottom: 25px;
           border-bottom: 1px solid #f0f0f0;
       }

       .timeline-item:last-child {
           border-bottom: none;
           margin-bottom: 0;
           padding-bottom: 0;
       }

       .timeline-dot {
           position: absolute;
           left: -30px;
           top: 5px;
           width: 18px;
           height: 18px;
           border-radius: 50%;
           background: #4D148C;
           border: 3px solid white;
           box-shadow: 0 0 0 3px #4D148C;
       }

       .timeline-item.pending .timeline-dot {
           background: #FF6600;
           box-shadow: 0 0 0 3px #FF6600;
           animation: pulse 2s infinite;
       }

       .timeline-date {
           font-size: 13px;
           color: #666;
           margin-bottom: 5px;
           font-weight: 500;
       }

       .timeline-status {
           font-size: 16px;
           font-weight: bold;
           color: #333;
           margin-bottom: 5px;
       }

       .timeline-location {
           font-size: 14px;
           color: #666;
       }

       /* Back Button */
       .back-btn {
           background: transparent;
           border: 2px solid #4D148C;
           color: #4D148C;
           padding: 10px 25px;
           border-radius: 4px;
           font-size: 14px;
           font-weight: bold;
           cursor: pointer;
           transition: all 0.3s;
           margin-bottom: 20px;
           display: inline-flex;
           align-items: center;
           gap: 8px;
       }

       .back-btn:hover {
           background: #4D148C;
           color: white;
       }

       /* Footer */
       .footer {
           background: #2d2d2d;
           color: #aaa;
           text-align: center;
           padding: 20px;
           margin-top: 50px;
           font-size: 12px;
       }

       /* Loading Spinner */
       .loading {
           display: none;
           width: 20px;
           height: 20px;
           border: 3px solid #f3f3f3;
           border-top: 3px solid #FF6600;
           border-radius: 50%;
           animation: spin 1s linear infinite;
           margin-left: 10px;
       }

       @keyframes spin {
           0% { transform: rotate(0deg); }
           100% { transform: rotate(360deg); }
       }

       /* Package Contents Styling */
       .contents-list {
           list-style: none;
           padding: 0;
           margin: 0;
       }

       .contents-list li {
           padding: 8px 0;
           border-bottom: 1px solid #eee;
           font-size: 15px;
           display: flex;
           align-items: center;
           gap: 10px;
       }

       .contents-list li:last-child {
           border-bottom: none;
       }

       .contents-list li::before {
           content: '✓';
           color: #4D148C;
           font-weight: bold;
           font-size: 18px;
       }

       .value-highlight {
           background: #e8f5e9;
           color: #2e7d32;
           padding: 2px 8px;
           border-radius: 4px;
           font-weight: bold;
           font-size: 14px;
       }

       /* Responsive */
       @media (max-width: 768px) {
           .tracking-landing {
               padding: 40px 20px;
               margin: 20px auto;
           }

           .tracking-input-group {
               flex-direction: column;
           }

           .details-section {
               grid-template-columns: 1fr;
           }
           
           .route-visual {
               flex-direction: column;
               gap: 20px;
           }
           
           .flight-path {
               width: 100%;
               transform: rotate(90deg);
               margin: 20px 0;
           }
       }
   </style>
</head>
<body>
   <!-- Header -->
   <header class="header">
       <div class="header-content">
           <div class="logo" onclick="goHome()">Fed<span>Ex</span></div>
           <nav class="nav-links">
               <a onclick="goHome()">Ship</a>
               <a onclick="goHome()">Track</a>
               <a onclick="goHome()">Manage</a>
               <a href="https://widget-page.smartsupp.com/widget/8ce683f92f4987a628d7c7548d09ab3a8d88d27b?ss-chat-settings" target="_blank">Support</a>
           </nav>
       </div>
   </header>

   <!-- Main Content -->
   <div class="container">
       
       <!-- LANDING PAGE - Tracking Input -->
       <div id="landingPage" class="tracking-landing">
           <h1>Track Your Shipment</h1>
           <p>Enter your FedEx tracking number to get real-time updates on your international shipment.</p>
           
           <div class="tracking-input-group">
               <input type="text" class="tracking-input" id="trackingInput" placeholder="Enter tracking number (e.g., 1Z999AA10123456784)" maxlength="18">
               <button class="track-btn" id="trackBtn" onclick="trackShipment()">
                   Track
                   <div class="loading" id="loadingSpinner"></div>
               </button>
           </div>
           
           <div class="error-message" id="errorMessage">
               ⚠️ Invalid tracking number. Please check and try again.
           </div>

           <div style="margin-top: 30px; padding: 15px; background: #fff3e0; border-radius: 8px; border-left: 4px solid #FF6600;">
               <p style="font-size: 14px; color: #666;">
                   <strong>Hint:</strong> Use tracking number <span style="font-family: monospace; background: #eee; padding: 2px 6px; border-radius: 3px;">1Z999AA10123456784</span> to view the Clara Boch shipment from USA to Germany.
               </p>
           </div>
       </div>

       <!-- STATUS PAGE - Shipment Details (Hidden by default) -->
       <div id="statusPage" class="status-page">
           <button class="back-btn" onclick="goHome()">
               ← Back to Tracking
           </button>

           <!-- Status Card -->
           <div class="status-card">
               <div class="status-header">
                   <div class="status-badge">Pending</div>
                   <div class="status-title">Shipment at Origin - Awaiting Departure</div>
                   <div class="tracking-number-display" id="displayTrackingNum">Tracking Number: 1Z999AA10123456784</div>
               </div>

               <!-- Progress Bar -->
               <div class="progress-section">
                   <div class="progress-bar">
                       <div class="progress-line">
                           <div class="progress-line-fill"></div>
                       </div>
                       <div class="progress-step completed">
                           <div class="step-circle">✓</div>
                           <div class="step-label">Picked Up</div>
                       </div>
                       <div class="progress-step active">
                           <div class="step-circle">●</div>
                           <div class="step-label">Pending</div>
                       </div>
                       <div class="progress-step">
                           <div class="step-circle">3</div>
                           <div class="step-label">In Transit</div>
                       </div>
                       <div class="progress-step">
                           <div class="step-circle">4</div>
                           <div class="step-label">Delivered</div>
                       </div>
                   </div>
               </div>

               <!-- Route Visualization -->
               <div class="route-section">
                   <div class="section-title">
                       <span>🌍</span> International Route - Awaiting Flight Departure
                   </div>
                   <div class="route-container">
                       <div class="route-visual">
                           <div class="location-box">
                               <div class="location-icon">🇺🇸</div>
                               <div class="location-city">Dallas/Fort Worth, TX</div>
                               <div class="location-country">United States</div>
                               <div style="font-size: 12px; color: #999; margin-top: 5px;">Current Location - DFW Airport</div>
                           </div>
                           
                           <div class="flight-path">
                               <div class="flight-line"></div>
                               <div class="plane-icon">✈️</div>
                               <div class="flight-info">Flight FX5032 - Scheduled</div>
                           </div>
                           
                           <div class="location-box">
                               <div class="location-icon">🇩🇪</div>
                               <div class="location-city">Frankfurt</div>
                               <div class="location-country">Germany</div>
                               <div style="font-size: 12px; color: #999; margin-top: 5px;">Destination Hub</div>
                           </div>
                       </div>
                       
                       <div class="status-pending-box">
                           <div class="pending-title">⏳ Flight Not Yet Departed</div>
                           <div class="pending-desc">
                               Shipment is currently at Dallas/Fort Worth International Airport (DFW), Texas.<br>
                               Awaiting scheduled departure on FedEx Flight FX5032 to Frankfurt, Germany.
                           </div>
                       </div>
                   </div>
               </div>

               <!-- Shipment Details -->
               <div class="details-section">
                   <div class="detail-card">
                       <div class="detail-label">Sender Information</div>
                       <div class="detail-value name">FedEx Ship Manager</div>
                       <div class="detail-value">United States</div>
                       <div class="detail-value highlight" style="margin-top: 10px;">
                           📧 sender.logistics@fedex.com
                       </div>
                       <div class="detail-value" style="margin-top: 10px; font-size: 14px;">
                           <strong>Service:</strong> FedEx International Priority<br>
                           <strong>Weight:</strong> 4.5 lbs / 2.04 kg<br>
                           <strong>Dimensions:</strong> 12" x 9" x 6"<br>
                           <strong>Ship Date:</strong> May 2, 2026
                       </div>
                   </div>
                   
                   <div class="detail-card receiver">
                       <div class="detail-label">Receiver Information</div>
                       <div class="detail-value name">Clara Boch</div>
                       <div class="detail-value">
                           Ander Weide, 3<br>
                           77652 Offenburg<br>
                           Germany
                       </div>
                       <div class="detail-value highlight" style="margin-top: 10px;">
                           📧 clara.mubanga@web.de
                       </div>
                       <div class="detail-value" style="margin-top: 5px; font-size: 14px;">
                           <strong>Phone:</strong> +49 172 3845597
                       </div>
                   </div>
               </div>

               <!-- Tracking History -->
               <div class="history-section">
                   <div class="section-title">
                       <span>📋</span> Shipment History
                   </div>
                   <div class="timeline">
                       <div class="timeline-item pending">
                           <div class="timeline-dot"></div>
                           <div class="timeline-date">May 2, 2026 - 14:30 CDT</div>
                           <div class="timeline-status">At Origin Facility - Awaiting Departure</div>
                           <div class="timeline-location">Dallas/Fort Worth International Airport (DFW), Texas, USA</div>
                       </div>
                       
                       <div class="timeline-item">
                           <div class="timeline-dot"></div>
                           <div class="timeline-date">May 2, 2026 - 10:15 CDT</div>
                           <div class="timeline-status">Arrived at FedEx Hub</div>
                           <div class="timeline-location">Dallas/Fort Worth, TX, United States</div>
                       </div>
                       
                       <div class="timeline-item">
                           <div class="timeline-dot"></div>
                           <div class="timeline-date">May 2, 2026 - 08:30 CDT</div>
                           <div class="timeline-status">In Transit to Airport</div>
                           <div class="timeline-location">Local Facility, Texas, United States</div>
                       </div>
                       
                       <div class="timeline-item">
                           <div class="timeline-dot"></div>
                           <div class="timeline-date">May 1, 2026 - 18:45 CDT</div>
                           <div class="timeline-status">Picked Up</div>
                           <div class="timeline-location">Shipper Location, Texas, United States</div>
                       </div>
                   </div>
               </div>
           </div>

           <!-- Package Contents -->
           <div style="background: white; padding: 25px; border-radius: 8px; box-shadow: 0 2px 15px rgba(0,0,0,0.08); margin-bottom: 30px;">
               <h3 style="color: #4D148C; margin-bottom: 20px; font-size: 18px;">📦 Package Contents</h3>
               <ul class="contents-list">
                   <li>1 × TESLA CAR</li>
                   <li>3 × Sealed Cash Box <span class="value-highlight">Worth $800,000.00 USD</span></li>
                   <li>3 × Starlink Network Kit</li>
                   <li>3 × iPhone 17</li>
               </ul>
               <div style="margin-top: 20px; padding: 15px; background: #f8f9fa; border-radius: 6px; border-left: 4px solid #4D148C;">
                   <div style="font-size: 12px; color: #666; margin-bottom: 5px;">Total Declared Value</div>
                   <div style="font-size: 24px; font-weight: bold; color: #2e7d32;">$800,000.00+ USD</div>
                   <div style="font-size: 12px; color: #999; margin-top: 5px;">Subject to customs duties and taxes</div>
               </div>
           </div>

           <!-- Additional Info -->
           <div style="background: white; padding: 20px; border-radius: 8px; box-shadow: 0 2px 15px rgba(0,0,0,0.08); margin-bottom: 30px;">
               <h3 style="color: #4D148C; margin-bottom: 15px;">📋 Shipping Details</h3>
               <div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(200px, 1fr)); gap: 15px;">
                   <div>
                       <div style="font-size: 12px; color: #666; margin-bottom: 5px;">Contents Type</div>
                       <div style="font-weight: 500;">High-Value Electronics & Vehicle</div>
                   </div>
                   <div>
                       <div style="font-size: 12px; color: #666; margin-bottom: 5px;">Declared Value</div>
                       <div style="font-weight: 500;">$800,000.00+ USD</div>
                   </div>
                   <div>
                       <div style="font-size: 12px; color: #666; margin-bottom: 5px;">Duties & Taxes</div>
                       <div style="font-weight: 500;">Recipient Responsible</div>
                   </div>
                   <div>
                       <div style="font-size: 12px; color: #666; margin-bottom: 5px;">Signature Required</div>
                       <div style="font-weight: 500;">Yes - Adult Signature Mandatory</div>
                   </div>
               </div>
           </div>
       </div>
   </div>

   <!-- Footer -->
   <footer class="footer">
       <p>© 2026 FedEx Corporation. All rights reserved. | Privacy Policy | Terms of Use</p>
       <p style="margin-top: 5px; font-size: 11px;">This is a demonstration page for educational purposes only.</p>
   </footer>

   <script>
       // Valid tracking numbers for demo
       const validTrackingNumbers = [
           '1Z999AA10123456784',
           '1Z888BB20234567891',
           '1Z777CC30345678908'
       ];

       // Default tracking number that shows Clara Boch shipment
       const DEFAULT_TRACKING = '1Z999AA10123456784';

       function trackShipment() {
           const input = document.getElementById('trackingInput');
           const errorMsg = document.getElementById('errorMessage');
           const trackBtn = document.getElementById('trackBtn');
           const spinner = document.getElementById('loadingSpinner');
           
           const trackingNum = input.value.trim().toUpperCase();
           
           // Show loading
           trackBtn.disabled = true;
           spinner.style.display = 'inline-block';
           
           // Simulate API delay
           setTimeout(() => {
               trackBtn.disabled = false;
               spinner.style.display = 'none';
               
               // Validate tracking number
               if (validTrackingNumbers.includes(trackingNum)) {
                   // Success - show status page
                   errorMsg.classList.remove('show');
                   showStatusPage(trackingNum);
               } else {
                   // Error - show error message
                   errorMsg.classList.add('show');
                   input.focus();
               }
           }, 800);
       }

       function showStatusPage(trackingNum) {
           document.getElementById('landingPage').style.display = 'none';
           document.getElementById('statusPage').classList.add('active');
           document.getElementById('displayTrackingNum').textContent = 'Tracking Number: ' + trackingNum;
           
           // Scroll to top
           window.scrollTo(0, 0);
       }

       function goHome() {
           document.getElementById('landingPage').style.display = 'block';
           document.getElementById('statusPage').classList.remove('active');
           document.getElementById('trackingInput').value = '';
           document.getElementById('errorMessage').classList.remove('show');
           window.scrollTo(0, 0);
       }

       // Allow Enter key to submit
       document.getElementById('trackingInput').addEventListener('keypress', function(e) {
           if (e.key === 'Enter') {
               trackShipment();
           }
       });
   </script>
</body>
</html>
