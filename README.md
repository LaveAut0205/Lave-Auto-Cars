# Lave-Auto-Cars
Daily Car Cleaning Services 
import React from "react"; import { Input } from "@/components/ui/input"; import { Button } from "@/components/ui/button"; import { Card, CardContent } from "@/components/ui/card"; import { motion } from "framer-motion";

export default function HomePage() { const handleRazorpay = (amount) => { const options = { key: "rzp_live_YourKeyID", // Replace with your Razorpay Live Key amount: amount * 100, currency: "INR", name: "Lave Auto Cars", description: "Car Cleaning Plan Payment", handler: function (response) { alert("Payment successful! Payment ID: " + response.razorpay_payment_id); }, prefill: { name: "", email: "", contact: "", }, theme: { color: "#0f766e", }, }; const rzp = new window.Razorpay(options); rzp.open(); };

const handleWhatsApp = (e) => { e.preventDefault(); const form = e.target; const name = form.name.value; const phone = form.phone.value; const location = form.location.value; const plan = form.plan.value; const message = Hi Lave Auto Cars, I’ve just booked the ${plan} plan.\nName: ${name}\nPhone: ${phone}\nLocation: ${location}; const encodedMessage = encodeURIComponent(message); window.open(https://wa.me/919971036610?text=${encodedMessage}, "_blank"); form.submit(); };

return ( <main className="min-h-screen bg-gray-100 p-4 flex flex-col items-center"> <motion.h1 className="text-4xl font-bold mt-10 text-center" initial={{ opacity: 0, y: -20 }} animate={{ opacity: 1, y: 0 }} transition={{ duration: 0.5 }} > Welcome to Lave Auto Cars - Daily Car Cleaning </motion.h1>

<motion.p 
    className="text-lg mt-4 mb-8 text-center max-w-xl"
    initial={{ opacity: 0 }} 
    animate={{ opacity: 1 }}
    transition={{ delay: 0.3 }}
  >
    Get your car sparkling clean every day with our reliable and affordable interior and exterior cleaning services. No hassle, just shine!
  </motion.p>

  <Card className="w-full max-w-md p-6 shadow-xl">
    <CardContent>
      <h2 className="text-2xl font-semibold text-center mb-4">Enter Your Car Number</h2>
      <form
        onSubmit={(e) => {
          e.preventDefault();
          const carNumber = e.target.carNumber.value;
          window.open(`https://parivahan.gov.in/rcdlstatus/?rc_number=${carNumber}`, '_blank');
        }}
        className="flex flex-col gap-4"
      >
        <Input
          type="text"
          name="carNumber"
          placeholder="e.g. DL8CAF5030"
          className="text-center text-lg"
          required
        />
        <Button type="submit" className="bg-blue-600 text-white hover:bg-blue-700">
          Check & Book Service
        </Button>
      </form>
    </CardContent>
  </Card>

  <section className="mt-10 grid grid-cols-1 md:grid-cols-2 gap-6 w-full max-w-4xl">
    <Card className="p-4">
      <h3 className="text-xl font-semibold mb-2">Interior Cleaning</h3>
      <p>Vacuuming, dashboard polishing, seat and mat cleaning to keep your car fresh inside.</p>
    </Card>
    <Card className="p-4">
      <h3 className="text-xl font-semibold mb-2">Exterior Washing</h3>
      <p>High-quality wash, dry, and shine using safe products for daily car care.</p>
    </Card>
  </section>

  <section className="mt-12 w-full max-w-2xl">
    <Card className="p-6">
      <h3 className="text-xl font-semibold mb-4 text-center">Booking & Pricing</h3>
      <p className="mb-2">Choose your service package:</p>
      <ul className="list-disc pl-6 mb-4">
        <li><strong>Daily</strong> - ₹30/day</li>
        <li><strong>Monthly</strong> - ₹800/month</li>
        <li><strong>Quarterly</strong> - ₹2300</li>
        <li><strong>Half-Yearly</strong> - ₹4600</li>
        <li><strong>Yearly</strong> - ₹9200</li>
      </ul>
      <form
        action="https://formsubmit.co/laveautocars@gmail.com"
        method="POST"
        onSubmit={handleWhatsApp}
        className="flex flex-col gap-4"
      >
        <Input type="text" name="name" placeholder="Your Name" required />
        <Input type="email" name="email" placeholder="Email Address" required />
        <Input type="tel" name="phone" placeholder="Phone Number" required />
        <Input type="text" name="location" placeholder="Location / Area / Pin Code" required />
        <select name="plan" className="p-2 rounded border">
          <option value="Daily">Daily - ₹30</option>
          <option value="Monthly">Monthly - ₹800</option>
          <option value="Quarterly">Quarterly - ₹2300</option>
          <option value="Half-Yearly">Half-Yearly - ₹4600</option>
          <option value="Yearly">Yearly - ₹9200</option>
        </select>
        <Button type="submit" className="bg-green-600 text-white hover:bg-green-700">Submit Booking</Button>
      </form>

      <div className="text-center mt-6">
        <p className="mb-2 text-gray-700 font-medium">Or pay directly online:</p>
        <div className="grid grid-cols-1 sm:grid-cols-2 gap-2">
          <Button onClick={() => handleRazorpay(30)} className="bg-indigo-500 hover:bg-indigo-600 text-white">Pay ₹30 (Daily)</Button>
          <Button onClick={() => handleRazorpay(800)} className="bg-indigo-500 hover:bg-indigo-600 text-white">Pay ₹800 (Monthly)</Button>
          <Button onClick={() => handleRazorpay(2300)} className="bg-indigo-500 hover:bg-indigo-600 text-white">Pay ₹2300 (Quarterly)</Button>
          <Button onClick={() => handleRazorpay(4600)} className="bg-indigo-500 hover:bg-indigo-600 text-white">Pay ₹4600 (Half-Yearly)</Button>
          <Button onClick={() => handleRazorpay(9200)} className="bg-indigo-500 hover:bg-indigo-600 text-white">Pay ₹9200 (Yearly)</Button>
        </div>
      </div>
    </Card>
  </section>

  <footer className="mt-16 text-center text-sm text-gray-600">
    &copy; {new Date().getFullYear()} Lave Auto Cars. All rights reserved.
  </footer>
</main>

); }

