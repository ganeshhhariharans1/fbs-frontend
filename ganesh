import React, { useState } from 'react';

const services = [
  { title: 'Marketing & Sales', price: '₹2,999/month' },
  { title: 'Food License (FSSAI)', price: '₹4,999' },
  { title: 'Logo Design', price: '₹999' },
  { title: 'Visiting Card Design', price: '₹499' },
  { title: 'Company Registration', price: '₹7,999' },
  { title: 'Video Editing (Basic)', price: '₹1,000/video' },
  { title: 'Ad Shoot Coordination', price: '₹9,999/project' },
  { title: 'Product Photo Shoot', price: '₹2,999/session' },
  { title: 'Social Media Handling', price: '₹4,999/month' },
  { title: 'Distribution', price: '₹14,999/project' },
  { title: 'Company Accounts Setup', price: '₹5,999' }
];

export default function App() {
  const [form, setForm] = useState({ name: '', email: '', phone: '', service: '' });
  const [status, setStatus] = useState('');

  const handleChange = e => setForm({ ...form, [e.target.name]: e.target.value });

  const handleSubmit = async e => {
    e.preventDefault();
    setStatus('Sending...');
    try {
      const res = await fetch('http://localhost:5000/send-lead', {
        method: 'POST',
        headers: { 'Content-Type': 'application/json' },
        body: JSON.stringify(form)
      });
      const data = await res.json();
      setStatus(data.message || 'Submitted!');
    } catch (err) {
      setStatus('Failed to send');
    }
  };

  return (
    <div className="min-h-screen bg-zinc-900 text-white px-4 py-10">
      <h1 className="text-3xl font-bold text-center mb-8">FBS Consultancy</h1>
      <h2 className="text-xl font-semibold mb-6">Helping Creators Think Like CEOs</h2>
      <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4">
        {services.map((service, idx) => (
          <div key={idx} className="bg-zinc-800 p-4 rounded-xl shadow">
            <h3 className="text-lg font-bold">{service.title}</h3>
            <p className="mb-2">{service.price}</p>
            <button
              className="bg-blue-600 px-3 py-2 rounded hover:bg-blue-700"
              onClick={() => setForm({ ...form, service: service.title })}>
              Request Now
            </button>
          </div>
        ))}
      </div>

      <form onSubmit={handleSubmit} className="max-w-md mx-auto mt-10 space-y-4">
        <input type="text" name="name" placeholder="Your Name" onChange={handleChange} required className="w-full p-2 rounded bg-zinc-800 text-white" />
        <input type="email" name="email" placeholder="Your Email" onChange={handleChange} required className="w-full p-2 rounded bg-zinc-800 text-white" />
        <input type="text" name="phone" placeholder="Your Phone" onChange={handleChange} required className="w-full p-2 rounded bg-zinc-800 text-white" />
        <input type="text" name="service" value={form.service} placeholder="Selected Service" readOnly className="w-full p-2 rounded bg-zinc-800 text-white" />
        <button type="submit" className="bg-green-600 px-4 py-2 rounded hover:bg-green-700 w-full">Submit</button>
        <p className="text-center text-sm">{status}</p>
      </form>

      <footer className="mt-12 text-center text-sm opacity-60">
        <p>Contact: buildwithfbs@gmail.com | WhatsApp: +91 7708521291</p>
        <a href="https://instagram.com/fbs_consultancy" target="_blank" rel="noopener noreferrer">
          Instagram: @fbs_consultancy
        </a>
      </footer>
    </div>
  );
}
