
# uni_rent
student housing platform
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>UniRent | Trusted Student Housing - UNIDEL Agbor</title>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <script src="https://js.paystack.co/v1/inline.js"></script>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Inter', sans-serif;
            background: #f5f7fb;
            color: #1a1f36;
        }

        /* Navigation */
        .navbar {
            background: white;
            box-shadow: 0 1px 3px rgba(0,0,0,0.05);
            position: sticky;
            top: 0;
            z-index: 100;
        }

        .nav-container {
            max-width: 1280px;
            margin: 0 auto;
            padding: 1rem 2rem;
            display: flex;
            justify-content: space-between;
            align-items: center;
            flex-wrap: wrap;
            gap: 1rem;
        }

        .logo {
            display: flex;
            align-items: center;
            gap: 0.75rem;
        }

        .logo-icon {
            background: linear-gradient(135deg, #0f3d2a, #1a6e4b);
            width: 45px;
            height: 45px;
            border-radius: 12px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.3rem;
            color: white;
        }

        .logo-text {
            font-size: 1.5rem;
            font-weight: 800;
            color: #0f3d2a;
        }

        .logo-badge {
            background: #fef3c7;
            color: #d97706;
            padding: 0.2rem 0.6rem;
            border-radius: 20px;
            font-size: 0.7rem;
            font-weight: 600;
        }

        .nav-buttons {
            display: flex;
            gap: 0.75rem;
        }

        .nav-btn {
            background: transparent;
            border: none;
            padding: 0.6rem 1.25rem;
            border-radius: 40px;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.2s;
            color: #4a5568;
        }

        .nav-btn:hover {
            background: #f0f2f5;
        }

        .nav-btn.active {
            background: #0f3d2a;
            color: white;
        }

        /* Views */
        .view {
            display: none;
        }

        .view.active {
            display: block;
        }

        .container {
            max-width: 1280px;
            margin: 0 auto;
            padding: 2rem;
        }

        /* Hero */
        .hero {
            text-align: center;
            padding: 2rem 0;
        }

        .hero h1 {
            font-size: 2.5rem;
            font-weight: 800;
            background: linear-gradient(135deg, #0f3d2a, #1a6e4b);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
            margin-bottom: 1rem;
        }

        .hero-badge {
            display: inline-block;
            background: #e6f7ed;
            color: #0f3d2a;
            padding: 0.3rem 1rem;
            border-radius: 30px;
            font-size: 0.8rem;
            font-weight: 600;
            margin-bottom: 1rem;
        }

        /* Filters */
        .filters {
            display: flex;
            gap: 1rem;
            margin-bottom: 2rem;
            flex-wrap: wrap;
            background: white;
            padding: 1rem;
            border-radius: 1rem;
            box-shadow: 0 1px 3px rgba(0,0,0,0.05);
        }

        .filters input, .filters select {
            flex: 1;
            min-width: 150px;
            padding: 0.75rem;
            border: 1px solid #e2e8f0;
            border-radius: 0.75rem;
            font-size: 0.9rem;
        }

        /* Property Grid */
        .property-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(340px, 1fr));
            gap: 1.5rem;
        }

        .property-card {
            background: white;
            border-radius: 1.25rem;
            overflow: hidden;
            transition: all 0.3s;
            box-shadow: 0 4px 12px rgba(0,0,0,0.05);
            cursor: pointer;
            position: relative;
        }

        .property-card:hover {
            transform: translateY(-4px);
            box-shadow: 0 12px 24px rgba(0,0,0,0.1);
        }

        .featured-badge {
            position: absolute;
            top: 12px;
            left: 12px;
            background: #f5b042;
            color: #1e3a2f;
            padding: 0.3rem 0.8rem;
            border-radius: 20px;
            font-size: 0.7rem;
            font-weight: 700;
            z-index: 2;
        }

        .property-image {
            height: 220px;
            background-size: cover;
            background-position: center;
            position: relative;
        }

        .price-badge {
            position: absolute;
            bottom: 12px;
            right: 12px;
            background: #0f3d2a;
            color: white;
            padding: 0.4rem 1rem;
            border-radius: 30px;
            font-weight: 700;
        }

        .property-content {
            padding: 1.25rem;
        }

        .property-title {
            font-size: 1.2rem;
            font-weight: 700;
            margin-bottom: 0.25rem;
        }

        .property-location {
            color: #64748b;
            font-size: 0.85rem;
            margin-bottom: 0.5rem;
        }

        .verified-badge {
            display: inline-flex;
            align-items: center;
            gap: 0.25rem;
            background: #e6f7ed;
            color: #0f3d2a;
            padding: 0.2rem 0.6rem;
            border-radius: 30px;
            font-size: 0.7rem;
            margin: 0.5rem 0;
        }

        .amenities {
            display: flex;
            flex-wrap: wrap;
            gap: 0.3rem;
            margin: 0.5rem 0;
        }

        .amenity-tag {
            background: #f0f2f5;
            padding: 0.2rem 0.5rem;
            border-radius: 15px;
            font-size: 0.7rem;
            color: #4a5568;
        }

        .contact-btn {
            width: 100%;
            background: #0f3d2a;
            color: white;
            border: none;
            padding: 0.6rem;
            border-radius: 0.75rem;
            font-weight: 600;
            cursor: pointer;
            margin-top: 0.5rem;
        }

        /* Forms */
        .form-card {
            background: white;
            border-radius: 1.25rem;
            padding: 1.75rem;
            margin-bottom: 1.5rem;
            box-shadow: 0 4px 12px rgba(0,0,0,0.05);
        }

        .form-group {
            margin-bottom: 1rem;
        }

        .form-group label {
            display: block;
            font-weight: 500;
            font-size: 0.85rem;
            margin-bottom: 0.25rem;
        }

        input, select, textarea {
            width: 100%;
            padding: 0.75rem;
            border: 1px solid #e2e8f0;
            border-radius: 0.75rem;
            font-size: 0.9rem;
        }

        .form-row {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 1rem;
        }

        .btn-primary {
            background: linear-gradient(135deg, #0f3d2a, #1a6e4b);
            color: white;
            border: none;
            padding: 0.9rem;
            border-radius: 0.75rem;
            font-weight: 700;
            cursor: pointer;
            width: 100%;
        }

        .btn-secondary {
            background: #f5b042;
            color: #0f3d2a;
            border: none;
            padding: 0.6rem 1rem;
            border-radius: 0.75rem;
            font-weight: 600;
            cursor: pointer;
        }

        /* Stats */
        .stats-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(180px, 1fr));
            gap: 1rem;
            margin-bottom: 1.5rem;
        }

        .stat-card {
            background: white;
            padding: 1.25rem;
            border-radius: 1rem;
            text-align: center;
        }

        .stat-number {
            font-size: 2rem;
            font-weight: 800;
            color: #0f3d2a;
        }

        /* Admin Table */
        .admin-table {
            overflow-x: auto;
        }

        table {
            width: 100%;
            border-collapse: collapse;
        }

        th, td {
            padding: 0.75rem;
            text-align: left;
            border-bottom: 1px solid #e2e8f0;
        }

        .approve-btn {
            background: #10b981;
            color: white;
            border: none;
            padding: 0.3rem 0.8rem;
            border-radius: 0.5rem;
            cursor: pointer;
        }

        .reject-btn {
            background: #ef4444;
            color: white;
            border: none;
            padding: 0.3rem 0.8rem;
            border-radius: 0.5rem;
            cursor: pointer;
            margin-left: 0.3rem;
        }

        .complaint-item {
            background: #fef3c7;
            padding: 0.75rem;
            border-radius: 0.75rem;
            margin-bottom: 0.5rem;
        }

        /* Modal */
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0,0,0,0.7);
            z-index: 1000;
            overflow-y: auto;
        }

        .modal-content {
            background: white;
            max-width: 600px;
            margin: 2rem auto;
            border-radius: 1.5rem;
            padding: 1.5rem;
            position: relative;
        }

        .close {
            position: absolute;
            right: 1.5rem;
            top: 1rem;
            font-size: 1.5rem;
            cursor: pointer;
        }

        .toast {
            position: fixed;
            bottom: 2rem;
            right: 2rem;
            background: #1e293b;
            color: white;
            padding: 0.75rem 1.25rem;
            border-radius: 0.75rem;
            z-index: 1000;
            animation: slideIn 0.3s ease;
        }

        @keyframes slideIn {
            from { transform: translateX(100%); opacity: 0; }
            to { transform: translateX(0); opacity: 1; }
        }

        .empty-state {
            text-align: center;
            padding: 3rem;
            color: #94a3b8;
        
    
        }

       
        .footer {
            text-align: center;
            padding: 2rem;
            color: #94a3b8;
            font-size: 0.8rem;
            border-top: 1px solid #e2e8f0;
            margin-top: 2rem;
        }

        @media (max-width: 768px) {
            .container { padding: 1rem; }
            .hero h1 { font-size: 1.8rem; }
            .form-row { grid-template-columns: 1fr; }
            .nav-container { flex-direction: column; }
        }
    </style>
</head>
<body>
    <nav class="navbar">
        <div class="nav-container">
            <div class="logo">
                <div class="logo-icon"><i class="fas fa-home"></i></div>
                <div>
                    <span class="logo-text">UniRent</span>
                    <span class="logo-badge">UNIDEL</span>
                </div>
            </div>
            <div class="nav-buttons">
                <button class="nav-btn active" onclick="switchView('student')"><i class="fas fa-search"></i> Find House</button>
                <button class="nav-btn" onclick="switchView('agent')"><i class="fas fa-plus-circle"></i> List Property</button>
                <button class="nav-btn" onclick="switchView('admin')"><i class="fas fa-shield-alt"></i> Admin</button>
            </div>
        </div>
    </nav>

    <div id="studentView" class="view active">
        <div class="container">
            <div class="hero">
                <span class="hero-badge"><i class="fas fa-check-circle"></i> Trusted by 1,000+ UNIDEL Students</span>
                <h1>Find Your Perfect Home <br>Near <span style="color:#1a6e4b;">University of Delta, Agbor</span></h1>
                <p style="color:#64748b; margin-top:0.5rem;">✓ Verified Agents ✓ No Scams ✓ Direct WhatsApp Contact</p>
            </div>
            <div class="filters">
                <input type="text" id="searchInput" placeholder="🔍 Search by location..." onkeyup="filterListings()">
                <select id="typeFilter" onchange="filterListings()">
                    <option value="">All Types</option>
                    <option value="Self-contained">Self-contained</option>
                    <option value="Shared hostel">Shared Hostel</option>
                    <option value="Flat/Apartment">Flat/Apartment</option>
                </select>
                <input type="number" id="priceFilter" placeholder="💰 Max price (₦)" onkeyup="filterListings()">
                <select id="sortFilter" onchange="filterListings()">
                    <option value="newest">Newest First</option>
                    <option value="price_low">Price: Low to High</option>
                    <option value="price_high">Price: High to Low</option>
                    <option value="popular">Most Viewed</option>
                </select>
            </div>
            <div id="propertyList" class="property-grid"></div>
        </div>
    </div>

    <div id="agentView" class="view">
        <div class="container">
            <div class="form-card">
                <h2><i class="fas fa-home"></i> List Your Property</h2>
                <p style="color:#64748b; margin-bottom:1.5rem;">Pay ₦2,000 via Paystack to list your property. Your listing will be reviewed by admin.</p>
                <div class="form-row">
                    <div class="form-group"><label>Property Title *</label><input type="text" id="propTitle" placeholder="e.g., Cozy Self-contained"></div>
                    <div class="form-group"><label>Rent Price (₦) *</label><input type="number" id="propPrice" placeholder="150000"></div>
                </div>
                <div class="form-row">
                    <div class="form-group"><label>Location *</label><input type="text" id="propLocation" placeholder="Alihame quarters"></div>
                    <div class="form-group"><label>Property Type *</label><select id="propType"><option>Self-contained</option><option>Shared hostel</option><option>Flat/Apartment</option></select></div>
                </div>
                <div class="form-group"><label>Description *</label><textarea id="propDesc" rows="3" placeholder="Bedrooms, bathrooms, amenities, security, water supply..."></textarea></div>
                <div class="form-row">
                    <div class="form-group"><label>Bedrooms</label><input type="number" id="propBedrooms" value="1"></div>
                    <div class="form-group"><label>Bathrooms</label><input type="number" id="propBathrooms" value="1"></div>
                </div>
                <div class="form-group"><label>Amenities (comma separated)</label><input type="text" id="propAmenities" placeholder="WiFi, Security, Water, Parking"></div>
                <div class="form-group"><label>Image URL</label><input type="text" id="propImage" placeholder="https://..."></div>
                <div class="form-row">
                    <div class="form-group"><label>Your Name *</label><input type="text" id="agentName"></div>
                    <div class="form-group"><label>Email *</label><input type="email" id="agentEmail"></div>
                </div>
                <div class="form-group"><label>WhatsApp Number *</label><input type="text" id="agentPhone" placeholder="0803 123 4567"></div>
                <button class="btn-primary" onclick="processPayment()"><i class="fas fa-credit-card"></i> Pay ₦2,000 & Submit</button>
            </div>
            <div class="form-card"><h3>Your Listings</h3><div id="agentListings"></div></div>
        </div>
    </div>

    <div id="adminView" class="view">
        <div class="container">
            <div class="form-card" id="adminLoginCard">
                <h2>Admin Login</h2>
                <input type="password" id="adminPassword" placeholder="Enter admin password">
                <button class="btn-primary" onclick="adminLogin()">Login</button>
                <p style="font-size:0.7rem; margin-top:0.5rem;">Contact owner for password</p>
            </div>
            <div id="adminPanel" style="display:none;">
                <div class="stats-grid" id="statsGrid"></div>
                <div class="form-card"><h3>⏳ Pending Approvals</h3><div id="pendingList"></div></div>
                <div class="form-card"><h3>⚠️ Complaints</h3><div id="complaintsList"></div></div>
                <div class="form-card"><h3>📊 All Listings</h3><div id="allListings"></div></div>
            </div>
        </div>
    </div>

    <div id="propertyModal" class="modal"><div class="modal-content"><span class="close" onclick="closeModal()">&times;</span><div id="modalContent"></div></div></div>
    <div class="footer"><p>© 2024 UniRent | Trusted Student Housing for University of Delta, Agbor</p></div>

    <script>
        // ========== CONFIGURATION ==========
        // REPLACE WITH YOUR REAL PAYSTACK PUBLIC KEY
        const PAYSTACK_PUBLIC_KEY = 'pk_live_pk_test_fb395d982eb8f4277871685e154a1d6fbd9cb6cdx'; // GET FROM https://dashboard.paystack.com
        
        let listings = [];
        let reviews = [];
        let complaints = [];
        let adminPassword = 'jeff123'; // CHANGE THIS
        
        // Load data from localStorage
        function loadData() {
            const stored = localStorage.getItem('unirent_data');
            if (stored) {
                const data = JSON.parse(stored);
                listings = data.listings || [];
                reviews = data.reviews || [];
                complaints = data.complaints || [];
            }
            if (listings.length === 0) {
                listings = [
                    { id: '1', title: 'Comfort Lodge', price: 120000, location: 'Alihame quarters', type: 'Self-contained', desc: '24/7 electricity, security guard, water supply', agent_name: 'Efe Realty', agent_phone: '08031234567', agent_email: 'efe@realty.com', status: 'approved', image: 'https://images.unsplash.com/photo-1560448204-e02f11c3d0e2?w=500', views: 245, bedrooms: 1, bathrooms: 1, amenities: ['Electricity', 'Water', 'Security'], featured: true, created_at: '2025-02-10' },
                    { id: '2', title: 'Divine Hostel', price: 85000, location: 'DBS Road', type: 'Shared hostel', desc: 'Female only, free wifi, shared kitchen', agent_name: 'Mrs. Joy Okon', agent_phone: '08123456789', agent_email: 'joy@email.com', status: 'approved', image: 'https://images.unsplash.com/photo-1554995207-c18c203602cb?w=500', views: 189, bedrooms: 4, bathrooms: 2, amenities: ['WiFi', 'Water', 'Security'], featured: false, created_at: '2025-02-05' },
                    { id: '3', title: 'Peace Estate', price: 200000, location: 'Agbor town', type: 'Flat/Apartment', desc: '2 bedroom flat, parking, quiet environment', agent_name: 'Godwin Properties', agent_phone: '09056781234', agent_email: 'godwin@props.com', status: 'approved', image: 'https://images.unsplash.com/photo-1512917774080-9991f1c4c750?w=500', views: 312, bedrooms: 2, bathrooms: 2, amenities: ['Parking', 'Security', 'Water'], featured: true, created_at: '2025-02-01' }
                ];
                saveData();
            }
        }

        function saveData() {
            localStorage.setItem('unirent_data', JSON.stringify({ listings, reviews, complaints }));
        }

        function getApprovedListings() {
            return listings.filter(l => l.status === 'approved');
        }

        function getListingRating(listingId) {
            const revs = reviews.filter(r => r.listingId === listingId);
            if (revs.length === 0) return 0;
            return (revs.reduce((a,b) => a + b.rating, 0) / revs.length).toFixed(1);
        }

        function renderListings(data) {
            const container = document.getElementById('propertyList');
            if (!data.length) { container.innerHTML = '<div class="empty-state"><i class="fas fa-home fa-3x"></i><p>No properties found.</p></div>'; return; }
            container.innerHTML = data.map(l => `
                <div class="property-card" onclick="openModal('${l.id}')">
                    ${l.featured ? '<div class="featured-badge"><i class="fas fa-star"></i> FEATURED</div>' : ''}
                    <div class="property-image" style="background-image: url('${l.image || 'https://images.unsplash.com/photo-1560448204-e02f11c3d0e2?w=500'}')">
                        <div class="price-badge">₦${l.price.toLocaleString()}<span style="font-size:0.7rem;">/month</span></div>
                    </div>
                    <div class="property-content">
                        <div class="property-title">${l.title}</div>
                        <div class="property-location"><i class="fas fa-map-marker-alt"></i> ${l.location}</div>
                        <div class="amenities">${l.amenities?.slice(0,3).map(a => `<span class="amenity-tag"><i class="fas fa-check"></i> ${a}</span>`).join('') || ''}</div>
                        <div class="verified-badge"><i class="fas fa-check-circle"></i> Verified Agent</div>
                        <div class="rating"><i class="fas fa-star" style="color:#f5b042;"></i> ${getListingRating(l.id)} (${reviews.filter(r => r.listingId === l.id).length} reviews)</div>
                        <button class="contact-btn" onclick="event.stopPropagation(); window.open('https://wa.me/${l.agent_phone.replace(/\D/g,'')}?text=Hi%20I%20saw%20${encodeURIComponent(l.title)}%20on%20UniRent','_blank')"><i class="fab fa-whatsapp"></i> Contact Agent</button>
                    </div>
                </div>
            `).join('');
        }

        function filterListings() {
            const search = document.getElementById('searchInput')?.value.toLowerCase() || '';
            const type = document.getElementById('typeFilter')?.value || '';
            const maxPrice = parseInt(document.getElementById('priceFilter')?.value) || Infinity;
            const sort = document.getElementById('sortFilter')?.value || 'newest';
            
            let filtered = getApprovedListings().filter(l => {
                return (!search || l.location.toLowerCase().includes(search) || l.title.toLowerCase().includes(search)) &&
                       (!type || l.type === type) &&
                       l.price <= maxPrice;
            });
            
            if (sort === 'price_low') filtered.sort((a,b) => a.price - b.price);
            else if (sort === 'price_high') filtered.sort((a,b) => b.price - a.price);
            else if (sort === 'popular') filtered.sort((a,b) => b.views - a.views);
            else filtered.sort((a,b) => new Date(b.created_at) - new Date(a.created_at));
            
            renderListings(filtered);
        }

        function openModal(id) {
            const l = listings.find(l => l.id === id);
            if (!l) return;
            l.views = (l.views || 0) + 1;
            saveData();
            
            const listingReviews = reviews.filter(r => r.listingId === id);
            document.getElementById('modalContent').innerHTML = `
                <h2>${l.title}</h2>
                <img src="${l.image || 'https://images.unsplash.com/photo-1560448204-e02f11c3d0e2?w=500'}" style="width:100%; border-radius:1rem; margin:1rem 0;">
                <div style="font-size:1.8rem; font-weight:800; color:#0f3d2a;">₦${l.price.toLocaleString()}<span style="font-size:1rem;">/month</span></div>
                <div style="margin:0.5rem 0;"><i class="fas fa-map-marker-alt"></i> ${l.location}</div>
                <div><strong>Type:</strong> ${l.type}</div>
                <div><strong>Bedrooms:</strong> ${l.bedrooms} | <strong>Bathrooms:</strong> ${l.bathrooms}</div>
                <div class="amenities" style="margin:0.5rem 0;"><strong>Amenities:</strong> ${l.amenities?.map(a => `<span class="amenity-tag">${a}</span>`).join('') || 'None listed'}</div>
                <div style="margin:1rem 0; color:#4a5568;">${l.desc}</div>
                <div style="background:#f8fafc; padding:1rem; border-radius:0.75rem; margin:1rem 0;">
                    <strong><i class="fas fa-user"></i> Agent:</strong> ${l.agent_name}<br>
                    <strong><i class="fas fa-phone"></i> Phone:</strong> ${l.agent_phone}
                </div>
                <button class="btn-primary" onclick="window.open('https://wa.me/${l.agent_phone.replace(/\D/g,'')}?text=Hi%20I%20saw%20${encodeURIComponent(l.title)}%20on%20UniRent','_blank')"><i class="fab fa-whatsapp"></i> Contact Agent on WhatsApp</button>
                <hr style="margin:1rem 0;">
                <h3>⭐ Reviews (${listingReviews.length})</h3>
                ${listingReviews.map(r => `<div style="background:#f8fafc; padding:0.75rem; border-radius:0.75rem; margin-bottom:0.5rem;"><strong>★ ${r.rating}/5</strong> - ${r.comment}<br><small>${r.date}</small></div>`).join('') || '<p>No reviews yet.</p>'}
                <select id="ratingSelect" style="width:100%; margin:0.5rem 0;"><option value="5">★★★★★ (5/5)</option><option value="4">★★★★☆ (4/5)</option><option value="3">★★★☆☆ (3/5)</option><option value="2">★★☆☆☆ (2/5)</option><option value="1">★☆☆☆☆ (1/5)</option></select>
                <textarea id="reviewText" placeholder="Write your review..." style="width:100%; margin-bottom:0.5rem;"></textarea>
                <button class="btn-secondary" onclick="submitReview('${id}')">Submit Review</button>
                <button class="btn-secondary" style="background:#ef4444; color:white; margin-left:0.5rem;" onclick="submitComplaint('${id}', '${l.agent_name}')">Report Complaint</button>
            `;
            document.getElementById('propertyModal').style.display = 'block';
        }

        function submitReview(id) {
            const rating = document.getElementById('ratingSelect').value;
            const comment = document.getElementById('reviewText').value;
            if (!comment) { alert('Please write a review'); return; }
            reviews.push({ listingId: id, rating: parseInt(rating), comment, date: new Date().toLocaleDateString() });
            saveData();
            closeModal();
            showToast('Review submitted!');
            filterListings();
        }

        function submitComplaint(id, agentName) {
            const complaint = prompt('Describe your complaint:');
            if (complaint) {
                complaints.push({ listingId: id, agent_name: agentName, complaint, date: new Date().toLocaleDateString() });
                saveData();
                showToast('Complaint submitted to admin');
            }
        }

        // REAL PAYSTACK PAYMENT
        function processPayment() {
            const title = document.getElementById('propTitle').value;
            const price = parseInt(document.getElementById('propPrice').value);
            const location = document.getElementById('propLocation').value;
            const type = document.getElementById('propType').value;
            const desc = document.getElementById('propDesc').value;
            const bedrooms = document.getElementById('propBedrooms').value;
            const bathrooms = document.getElementById('propBathrooms').value;
            const amenities = document.getElementById('propAmenities').value.split(',').map(a => a.trim());
            const image = document.getElementById('propImage').value;
            const agentName = document.getElementById('agentName').value;
            const agentEmail = document.getElementById('agentEmail').value;
            const agentPhone = document.getElementById('agentPhone').value;

            if (!title || !price || !location || !agentName || !agentEmail || !agentPhone) {
                alert('Please fill all required fields');
                return;
            }

            const listingData = { title, price, location, type, desc, bedrooms, bathrooms, amenities, image, agent_name: agentName, agent_email: agentEmail, agent_phone: agentPhone };

            const handler = PaystackPop.setup({
                key: PAYSTACK_PUBLIC_KEY,
                email: agentEmail,
                amount: 200000,
                currency: 'NGN',
                ref: 'UNIRENT_' + Date.now() + '_' + Math.random().toString(36).substr(2, 8),
                callback: function(response) {
                    const newListing = {
                        id: Date.now().toString(),
                        ...listingData,
                        status: 'pending',
                        views: 0,
                        featured: false,
                        created_at: new Date().toISOString().split('T')[0]
                    };
                    listings.push(newListing);
                    saveData();
                    showToast('Payment successful! Listing submitted for approval.');
                    document.querySelectorAll('#agentView input, #agentView textarea').forEach(el => el.value = '');
                    document.getElementById('propBedrooms').value = '1';
                    document.getElementById('propBathrooms').value = '1';
                    loadAgentListings();
                },
                onClose: function() { alert('Payment cancelled.'); }
            });
            handler.openIframe();
        }

        function loadAgentListings() {
            const email = document.getElementById('agentEmail')?.value;
            if (!email) { document.getElementById('agentListings').innerHTML = '<div class="empty-state">Enter your email to see your listings</div>'; return; }
            const myListings = listings.filter(l => l.agent_email === email);
            document.getElementById('agentListings').innerHTML = myListings.length ? myListings.map(l => `
                <div style="border-bottom:1px solid #e2e8f0; padding:0.75rem;">
                    <strong>${l.title}</strong> - ₦${l.price.toLocaleString()}<br>
                    Status: <span style="color:${l.status === 'approved' ? '#10b981' : l.status === 'rejected' ? '#ef4444' : '#f59e0b'}">${l.status.toUpperCase()}</span>
                    ${l.status === 'approved' ? `<br><small>👁️ ${l.views} views</small>` : ''}
                </div>
            `).join('') : '<div class="empty-state">No listings yet</div>';
        }

        // Admin functions
        function adminLogin() {
            const pwd = document.getElementById('adminPassword').value;
            if (pwd === adminPassword) {
                document.getElementById('adminLoginCard').style.display = 'none';
                document.getElementById('adminPanel').style.display = 'block';
                loadAdminPanel();
                showToast('Admin login successful');
            } else { alert('Wrong password'); }
        }

        function loadAdminPanel() {
            const approved = listings.filter(l => l.status === 'approved');
            const pending = listings.filter(l => l.status === 'pending');
            document.getElementById('statsGrid').innerHTML = `
                <div class="stat-card"><div class="stat-number">${approved.length}</div><div>Active Listings</div></div>
                <div class="stat-card"><div class="stat-number">${pending.length}</div><div>Pending</div></div>
                <div class="stat-card"><div class="stat-number">₦${(approved.length * 2000).toLocaleString()}</div><div>Revenue</div></div>
                <div class="stat-card"><div class="stat-number">${complaints.length}</div><div>Complaints</div></div>
            `;
            document.getElementById('pendingList').innerHTML = pending.length ? `
                <div class="admin-table"><table><th>Title</th><th>Agent</th><th>Price</th><th>Actions</th></tr>
                ${pending.map(l => `<tr><td>${l.title}</td><td>${l.agent_name}<br><small>${l.agent_phone}</small></td><td>₦${l.price.toLocaleString()}</td><td><button class="approve-btn" onclick="approveListing('${l.id}')">Approve</button><button class="reject-btn" onclick="rejectListing('${l.id}')">Reject</button></td></tr>`).join('')}
                </div>` : '<div class="empty-state">No pending listings</div>';
            
            document.getElementById('complaintsList').innerHTML = complaints.length ? complaints.map(c => `<div class="complaint-item"><strong>Against: ${c.agent_name}</strong><br>${c.complaint}<br><small>${c.date}</small></div>`).join('') : '<div class="empty-state">No complaints</div>';
            document.getElementById('allListings').innerHTML = approved.map(l => `<div style="border-bottom:1px solid #ddd; padding:0.5rem;"><strong>${l.title}</strong> - ₦${l.price.toLocaleString()} - 👁️ ${l.views} views</div>`).join('');
        }

        function approveListing(id) { const l = listings.find(l => l.id === id); if(l){ l.status = 'approved'; saveData(); loadAdminPanel(); filterListings(); showToast(`✅ ${l.title} approved`); } }
        function rejectListing(id) { if(confirm('Reject?')){ const l = listings.find(l => l.id === id); l.status = 'rejected'; saveData(); loadAdminPanel(); showToast(`❌ Rejected`); } }

        function switchView(view) {
            document.querySelectorAll('.view').forEach(v => v.classList.remove('active'));
            document.getElementById(`${view}View`).classList.add('active');
            document.querySelectorAll('.nav-btn').forEach(b => b.classList.remove('active'));
            event.target.classList.add('active');
            if (view === 'student') filterListings();
            if (view === 'agent') loadAgentListings();
        }

        function closeModal() { document.getElementById('propertyModal').style.display = 'none'; }
        function showToast(msg) { const t = document.createElement('div'); t.className = 'toast'; t.innerHTML = msg; document.body.appendChild(t); setTimeout(() => t.remove(), 3000); }

        loadData();
        filterListings();
        document.getElementById('agentEmail')?.addEventListener('input', loadAgentListings);
    </script>
</body>
</html>
