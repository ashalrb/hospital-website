const doctors = {
     general: [
         { name: "Dr. John Smith", qualification: "MD, Internal Medicine", image: "https://randomuser.me/api/portraits/men/1.jpg", staff: ["Nurse Sarah", "Nurse Michael"] },
         { name: "Dr. Sarah Johnson", qualification: "MD, Family Medicine", image: "https://randomuser.me/api/portraits/women/1.jpg", staff: ["Nurse David", "Nurse Emma"] }
     ],
     gynaecology: [
         { name: "Dr. Emily Brown", qualification: "MD, Obstetrics & Gynecology", image: "https://randomuser.me/api/portraits/women/2.jpg", staff: ["Nurse Alice", "Nurse John"] },
         { name: "Dr. Lisa Davis", qualification: "MD, Reproductive Medicine", image: "https://randomuser.me/api/portraits/women/3.jpg", staff: ["Nurse Robert", "Nurse Mary"] }
     ],
     radiology: [
         { name: "Dr. Michael Wilson", qualification: "MD, Diagnostic Radiology", image: "https://randomuser.me/api/portraits/men/2.jpg", staff: ["Tech James", "Tech Linda"] },
         { name: "Dr. Robert Taylor", qualification: "MD, Interventional Radiology", image: "https://randomuser.me/api/portraits/men/3.jpg", staff: ["Tech William", "Tech Susan"] }
     ],
     dermatology: [
         { name: "Dr. Jessica Martinez", qualification: "MD, Dermatology", image: "https://randomuser.me/api/portraits/women/4.jpg", staff: ["Nurse Patricia", "Nurse Thomas"] },
         { name: "Dr. David Anderson", qualification: "MD, Cosmetic Dermatology", image: "https://randomuser.me/api/portraits/men/4.jpg", staff: ["Nurse Jennifer", "Nurse Richard"] }
     ],
     neurology: [
         { name: "Dr. James White", qualification: "MD, Neurology", image: "https://randomuser.me/api/portraits/men/5.jpg", staff: ["Nurse Elizabeth", "Nurse Charles"] },
         { name: "Dr. Patricia Moore", qualification: "MD, Neurophysiology", image: "https://randomuser.me/api/portraits/women/5.jpg", staff: ["Nurse Margaret", "Nurse Joseph"] }
     ]
 };
 
 const prices = {
     op: {
         consultation: 100,
         general: 150,
         gynaecology: 200,
         radiology: 300,
         dermatology: 180,
         neurology: 250
     },
     ip: {
         general: { base: 200, general: 100, semi: 200, private: 300 },
         gynaecology: { base: 250, general: 100, semi: 200, private: 300 },
         radiology: { base: 350, general: 100, semi: 200, private: 300 },
         dermatology: { base: 280, general: 100, semi: 200, private: 300 },
         neurology: { base: 400, general: 100, semi: 200, private: 300 }
     }
 };
 
 function showDoctors(department) {
     const doctorsList = document.getElementById('doctors-list');
     const doctorsSection = document.getElementById('doctors');
     
     doctorsList.innerHTML = '';
     doctors[department].forEach(doctor => {
         const doctorCard = document.createElement('div');
         doctorCard.className = 'doctor-card';
         doctorCard.innerHTML = `
             <img src="${doctor.image}" alt="${doctor.name}" class="doctor-image">
             <h3>${doctor.name}</h3>
             <p class="qualification">${doctor.qualification}</p>
             <div class="staff-list">
                 <h4>Supporting Staff:</h4>
                 <ul>
                     ${doctor.staff.map(staff => `<li>${staff}</li>`).join('')}
                 </ul>
             </div>
         `;
         doctorsList.appendChild(doctorCard);
     });
     
     doctorsSection.classList.remove('hidden');
     doctorsSection.scrollIntoView({ behavior: 'smooth' });
 }
 
 document.getElementById('patient-type').addEventListener('change', function(e) {
     const roomSelection = document.getElementById('room-selection');
     if (e.target.value === 'ip') {
         roomSelection.classList.remove('hidden');
     } else {
         roomSelection.classList.add('hidden');
     }
 });
 
 // Form validation function
 function validateForm() {
     const name = document.getElementById('name').value.trim();
     const email = document.getElementById('email').value.trim();
     const phone = document.getElementById('phone').value.trim();
     const dob = document.getElementById('dob').value;
     const department = document.getElementById('department').value;
     const symptoms = document.getElementById('symptoms').value.trim();
 
     if (!name || !email || !phone || !dob || !department || !symptoms) {
         alert('Please fill in all required fields');
         return false;
     }
 
     if (!email.match(/^[^\s@]+@[^\s@]+\.[^\s@]+$/)) {
         alert('Please enter a valid email address');
         return false;
     }
 
     if (!phone.match(/^\d{10}$/)) {
         alert('Please enter a valid 10-digit phone number');
         return false;
     }
 
     return true;
 }
 
 // Calculate fees based on patient type and department
 function calculateFees(patientType, department, roomType = null) {
     let totalCost = 0;
 
     if (patientType === 'op') {
         totalCost = prices.op.consultation + prices.op[department];
     } else {
         totalCost = prices.ip[department].base + prices.ip[department][roomType];
     }
 
     return totalCost;
 }
 
 // Booking form submission handler
 document.getElementById('booking-form').addEventListener('submit', function(e) {
     e.preventDefault();
     
     if (!validateForm()) return;
 
     const patientType = document.getElementById('patient-type').value;
     const department = document.getElementById('department').value;
     const roomType = patientType === 'ip' ? document.getElementById('room-type').value : null;
     
     const totalCost = calculateFees(patientType, department, roomType);
     
     const bookingDetails = `
         Appointment booked successfully!
         Department: ${department.charAt(0).toUpperCase() + department.slice(1)}
         Patient Type: ${patientType.toUpperCase()}
         ${roomType ? `Room Type: ${roomType.charAt(0).toUpperCase() + roomType.slice(1)}\n` : ''}
         Estimated Cost: $${totalCost}
     `;
     
     alert(bookingDetails);
     this.reset();
     document.getElementById('room-selection').classList.add('hidden');
 });
