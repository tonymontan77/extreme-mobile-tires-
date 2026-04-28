import { useEffect, useMemo, useState } from 'react';

const GOOGLE_MAPS_URL = 'https://maps.app.goo.gl/LhVSyPpvzWAJtJNL8';
const PHONE_DISPLAY = '1-800-682-0626';
const PHONE_TEL = '9706820626';
const SMS_TEXT = 'Hi Extreme Mobile Tires, I need mobile tire, truck tire, trailer tire, or OTR tire service. My location is:';

const fallbackReviews = [
  { name: 'Google Customer', rating: 5, text: 'Fast, professional mobile tire service. Highly recommended.' },
  { name: 'Google Customer', rating: 5, text: 'Reliable roadside tire help and great communication.' },
  { name: 'Google Customer', rating: 5, text: 'Quick response and quality service at my location.' },
];

const services = [
  { title: 'Emergency Flat Tire Help', desc: 'Fast roadside tire assistance when you are stuck and need help now.' },
  { title: 'Mobile Tire Repair', desc: 'Professional tire repair and patching service at your location.' },
  { title: 'Mobile Truck Tire Repair', desc: 'Roadside tire service for semis, box trucks, work trucks, commercial vehicles, and heavy-duty trucks.' },
  { title: 'OTR Tire Service', desc: 'Off-the-road tire service for big trucks, heavy equipment, machines, construction sites, farms, and industrial yards.' },
  { title: 'Fleet + Trailer Tire Service', desc: 'Dependable mobile tire support for fleets, trailers, vans, delivery trucks, and commercial operations.' },
  { title: 'Tire Installation', desc: 'Tire mounting and installation brought directly to your home, job, business, yard, shop, or roadside.' },
];

const coverage = [
  'Nationwide Mobile Tire Service',
  'Mobile Truck Tire Repair Nationwide',
  'Big Truck Tire Repair',
  'OTR Tire Service for Big Trucks & Machines',
  'Heavy Equipment Tire Service',
  'Fleet + Trailer Tire Service',
  'Emergency Roadside Tire Service Nationwide',
  'Commercial Truck Tire Repair',
  'Flat Tire Help Near You Nationwide',
  'Mobile Tire Installation Anywhere in the U.S.',
];

const faqs = [
  { q: 'Do you come to my location?', a: 'Yes. We provide mobile tire service at homes, workplaces, businesses, parking lots, yards, job sites, and roadside locations.' },
  { q: 'Do you service commercial trucks?', a: 'Yes. We provide mobile truck tire repair for semis, box trucks, work trucks, trailers, fleet vehicles, and big trucks.' },
  { q: 'Do you handle OTR tires and machines?', a: 'Yes. We offer OTR tire service for big trucks, heavy equipment, machines, construction sites, farms, yards, and industrial needs.' },
  { q: 'Do you work on fleets and trailers?', a: 'Yes. We provide fleet tire service and trailer tire service for commercial vehicles, delivery trucks, work trucks, and roadside breakdowns.' },
  { q: 'Can I call for emergency tire help?', a: 'Yes. Emergency tire service is available 24/7. Call or text your location, vehicle type, tire size if available, and tire issue for fast dispatch.' },
  { q: 'Do you repair and replace tires?', a: 'Yes. We help with flat repairs, tire replacement, installation, roadside tire service, truck tires, trailer tires, and OTR tires.' },
];

function setMetaTag(name, content) {
  if (typeof document === 'undefined') return;

  let tag = document.querySelector(`meta[name="${name}"]`);
  if (!tag) {
    tag = document.createElement('meta');
    tag.setAttribute('name', name);
    document.head.appendChild(tag);
  }

  tag.setAttribute('content', content);
}

function runSmokeTests() {
  console.assert(GOOGLE_MAPS_URL.startsWith('https://maps.app.goo.gl/'), 'Google Maps URL should be valid.');
  console.assert(PHONE_TEL === '9706820626', 'Phone tel link should call the real number.');
  console.assert(PHONE_DISPLAY === '1-800-682-0626', 'Displayed phone number should be the 1-800 style number.');
  console.assert(Array.isArray(services) && services.length >= 6, 'Services should include at least 6 items.');
  console.assert(Array.isArray(coverage) && coverage.length >= 5, 'Coverage should include nationwide targeting.');
  console.assert(Array.isArray(faqs) && faqs.length >= 4, 'FAQ section should include useful conversion questions.');
}

export default function Website() {
  const [showIntro, setShowIntro] = useState(true);
  const [introIn, setIntroIn] = useState(false);
  const [reviews, setReviews] = useState(fallbackReviews);

  const phoneHref = useMemo(() => `tel:${PHONE_TEL}`, []);
  const smsHref = useMemo(() => `sms:${PHONE_TEL}?body=${encodeURIComponent(SMS_TEXT)}`, []);

  useEffect(() => {
    const animationTimer = setTimeout(() => setIntroIn(true), 50);
    const closeTimer = setTimeout(() => setShowIntro(false), 3500);

    return () => {
      clearTimeout(animationTimer);
      clearTimeout(closeTimer);
    };
  }, []);

  useEffect(() => {
    document.title = 'Mobile Tire Repair, Truck Tire Repair & OTR Tire Service | Extreme Mobile Tires';
    setMetaTag(
      'description',
      '24/7 mobile tire repair, mobile truck tire repair, OTR tire service, heavy equipment tire service, trailer tire service, fleet tire service, flat tire service, tire installation and roadside assistance. Fast response. Call Extreme Mobile Tires now.'
    );
    setMetaTag(
      'keywords',
      'mobile tire repair near me, mobile truck tire repair, OTR tire service, big truck tire repair, heavy equipment tire service, machine tire service, trailer tire service, fleet tire service, commercial truck tire repair, roadside tire repair, mobile tire installation, emergency tire service, nationwide mobile tire service'
    );
    runSmokeTests();
  }, []);

  useEffect(() => {
    async function loadGoogleReviews() {
      try {
        const response = await fetch('/api/google-reviews');
        if (!response.ok) return;
        const data = await response.json();
        if (Array.isArray(data.reviews) && data.reviews.length > 0) {
          setReviews(data.reviews);
        }
      } catch (error) {
        // Keep fallback reviews visible when live reviews are not connected yet.
      }
    }

    loadGoogleReviews();
  }, []);

  return (
    <div className="min-h-screen bg-[#f7f9fc] text-slate-950 font-sans selection:bg-blue-200">
      {showIntro && (
        <div className="fixed inset-0 z-50 flex items-center justify-center bg-slate-950/80 backdrop-blur-xl px-4">
          <div
            className={`bg-white text-slate-950 rounded-[2rem] p-8 max-w-md w-full text-center shadow-2xl transform transition-all duration-500 border border-white/60 ${
              introIn ? 'translate-y-0 opacity-100' : 'translate-y-10 opacity-0'
            }`}
          >
            <div className="mx-auto mb-4 h-14 w-14 rounded-2xl bg-gradient-to-br from-blue-600 to-slate-950 flex items-center justify-center text-white font-black text-xl">
              EM
            </div>
            <p className="text-blue-700 font-black uppercase tracking-[0.2em] text-sm">Extreme Mobile Tires</p>
            <h2 className="text-3xl font-black mt-2">We Come To You</h2>
            <p className="mt-4 text-slate-600">
              Flat tire? Truck tire? OTR tire? Professional mobile tire service for cars, trucks, trailers, fleets, and machines at your location.
            </p>
            <div className="mt-6 flex flex-col gap-3">
              <a href={phoneHref} className="bg-blue-700 hover:bg-blue-800 text-white px-6 py-3 rounded-2xl font-bold shadow-lg shadow-blue-700/20">
                Call {PHONE_DISPLAY}
              </a>
              <a href={smsHref} className="bg-slate-950 hover:bg-slate-800 text-white px-6 py-3 rounded-2xl font-bold">
                Text Now
              </a>
              <button type="button" onClick={() => setShowIntro(false)} className="text-slate-500 underline">
                Continue to Website
              </button>
            </div>
          </div>
        </div>
      )}

      <a
        href={smsHref}
        className="hidden md:flex fixed right-0 top-1/2 -translate-y-1/2 bg-blue-700 hover:bg-blue-800 text-white px-4 py-4 rounded-l-2xl font-black shadow-2xl z-40 tracking-wide"
        style={{ writingMode: 'vertical-rl', textOrientation: 'mixed' }}
        aria-label="Text Extreme Mobile Tires now"
      >
        TEXT NOW
      </a>

      <header className="bg-white/90 backdrop-blur-xl sticky top-0 z-30 border-b border-slate-200/70 shadow-sm">
        <div className="bg-slate-950 text-white text-center text-sm py-2 font-semibold">
          Nationwide Mobile Tire • Truck Tire • OTR Tire Service • 24/7 Emergency Dispatch
        </div>
        <div className="max-w-7xl mx-auto px-5 md:px-8 py-4 flex justify-between items-center gap-4">
          <div className="flex items-center gap-3">
            <div className="h-12 w-12 rounded-2xl bg-gradient-to-br from-blue-600 to-slate-950 flex items-center justify-center text-white font-black">
              EM
            </div>
            <div>
              <h1 className="text-xl md:text-2xl font-black tracking-tight text-slate-950">Extreme Mobile Tires</h1>
              <p className="text-xs md:text-sm text-slate-500">Mobile Tire • Truck Tire • OTR Tire Service</p>
            </div>
          </div>
          <div className="hidden md:flex items-center gap-3">
            <a href={smsHref} className="border border-slate-300 text-slate-950 px-5 py-3 rounded-2xl font-bold hover:bg-slate-100">
              Text Now
            </a>
            <a href={phoneHref} className="bg-blue-700 hover:bg-blue-800 text-white px-5 py-3 rounded-2xl font-bold shadow-lg shadow-blue-700/20 whitespace-nowrap">
              Call {PHONE_DISPLAY}
            </a>
          </div>
          <a href={phoneHref} className="md:hidden bg-blue-700 text-white px-4 py-3 rounded-2xl font-bold shadow-lg shadow-blue-700/20">
            CALL
          </a>
        </div>
      </header>

      <section className="relative overflow-hidden bg-slate-950 text-white">
        <div className="absolute inset-0">
          <img
            src="https://images.unsplash.com/photo-1486262715619-67b85e0b08d3?auto=format&fit=crop&w=1800&q=80"
            alt="Roadside tire service"
            className="h-full w-full object-cover opacity-35"
          />
        </div>
        <div className="absolute inset-0 bg-gradient-to-br from-slate-950 via-slate-950/85 to-blue-950/80" />
        <div className="absolute inset-0 opacity-30 bg-[radial-gradient(circle_at_top_left,_#60a5fa,_transparent_32%),radial-gradient(circle_at_bottom_right,_white,_transparent_20%)]" />

        <div className="relative max-w-7xl mx-auto px-5 md:px-8 py-24 md:py-32 grid lg:grid-cols-[1.1fr_0.9fr] gap-12 items-center min-h-[760px]">
          <div>
            <p className="inline-flex items-center justify-center bg-white/10 border border-white/20 text-white px-5 py-2 rounded-full text-xs md:text-sm font-black uppercase tracking-[0.18em] mb-6 backdrop-blur">
              24/7 Emergency Dispatch
            </p>
            <h1 className="text-5xl md:text-7xl font-black leading-[0.95] tracking-tight">
              Mobile Tire, Truck Tire & OTR Service That Comes To You
            </h1>
            <p className="mt-6 text-xl md:text-2xl text-blue-100 max-w-3xl">
              Flat tire repair, truck tire repair, OTR tire service, trailer tire service, heavy equipment tire help, roadside help, and fleet service — fast, reliable, and professional nationwide.
            </p>
            <div className="mt-8 flex flex-col sm:flex-row gap-4">
              <a href={phoneHref} className="inline-block text-center bg-white text-blue-700 hover:bg-blue-50 px-8 py-4 rounded-2xl font-black text-lg shadow-2xl">
                Call {PHONE_DISPLAY}
              </a>
              <a href={smsHref} className="inline-block text-center bg-blue-700 hover:bg-blue-800 border border-blue-400/30 text-white px-8 py-4 rounded-2xl font-black text-lg shadow-2xl">
                Text Now
              </a>
            </div>
            <div className="mt-10 flex flex-wrap gap-3 text-sm text-blue-100">
              <span className="bg-white/10 border border-white/15 rounded-full px-4 py-2 backdrop-blur">✓ No towing needed</span>
              <span className="bg-white/10 border border-white/15 rounded-full px-4 py-2 backdrop-blur">✓ Emergency roadside help</span>
              <span className="bg-white/10 border border-white/15 rounded-full px-4 py-2 backdrop-blur">✓ Truck, trailer & OTR tires</span>
              <span className="bg-white/10 border border-white/15 rounded-full px-4 py-2 backdrop-blur">✓ Professional equipment</span>
            </div>
          </div>

          <div className="bg-white/10 border border-white/15 backdrop-blur-xl rounded-[2rem] p-6 md:p-8 shadow-2xl">
            <p className="text-blue-200 font-black uppercase tracking-[0.2em] text-xs">Fast Dispatch</p>
            <h2 className="text-3xl font-black mt-2">Need tire help right now?</h2>
            <p className="text-blue-100 mt-3">
              Send your location, vehicle type, tire size if available, and tire issue. We help cars, trucks, trailers, fleets, and OTR equipment.
            </p>
            <div className="mt-6 grid grid-cols-3 gap-3 text-center">
              <div className="bg-white/10 rounded-2xl p-4">
                <p className="font-black text-2xl">24/7</p>
                <p className="text-xs text-blue-100">Help</p>
              </div>
              <div className="bg-white/10 rounded-2xl p-4">
                <p className="font-black text-2xl">Fast</p>
                <p className="text-xs text-blue-100">Arrival</p>
              </div>
              <div className="bg-white/10 rounded-2xl p-4">
                <p className="font-black text-2xl">Pro</p>
                <p className="text-xs text-blue-100">Service</p>
              </div>
            </div>
            <a href="#request" className="mt-6 block text-center bg-white text-slate-950 rounded-2xl py-4 font-black">
              Get Free Quote
            </a>
          </div>
        </div>
      </section>

      <section className="max-w-7xl mx-auto px-5 md:px-8 -mt-14 relative z-10 grid md:grid-cols-4 gap-5">
        {[
          ['5+', 'Years Experience'],
          ['500+', 'Customers Served'],
          ['24/7', 'Emergency Service'],
          ['Nationwide', 'Coverage'],
        ].map(([num, label]) => (
          <div key={label} className="bg-white border border-slate-200 p-6 rounded-[1.75rem] shadow-xl text-center">
            <h4 className="text-3xl font-black text-blue-700">{num}</h4>
            <p className="text-slate-600 font-medium">{label}</p>
          </div>
        ))}
      </section>

      <section className="max-w-7xl mx-auto px-5 md:px-8 py-20">
        <div className="grid lg:grid-cols-[0.9fr_1.1fr] gap-10 items-center">
          <div>
            <p className="text-blue-700 font-black uppercase tracking-[0.2em] text-sm">Premium Mobile Service</p>
            <h2 className="text-4xl md:text-6xl font-black mt-3 tracking-tight">
              A tire shop on wheels for cars, trucks, trailers & machines.
            </h2>
            <p className="text-slate-600 mt-5 text-lg">
              No waiting rooms. No tow truck. No wasted day. We bring tire repair, truck tire service, trailer tire help, fleet support, and OTR tire service straight to your location.
            </p>
            <a href={phoneHref} className="inline-block mt-7 bg-blue-700 text-white px-7 py-4 rounded-2xl font-black shadow-xl shadow-blue-700/20">
              Call for Service
            </a>
          </div>
          <div className="grid sm:grid-cols-2 gap-5">
            <img
              src="https://images.unsplash.com/photo-1597764690527-15bea4c581c9?auto=format&fit=crop&w=900&q=80"
              alt="Tire service closeup"
              className="rounded-[2rem] h-72 w-full object-cover shadow-xl"
            />
            <img
              src="https://images.unsplash.com/photo-1619642751034-765dfdf7c58e?auto=format&fit=crop&w=900&q=80"
              alt="Roadside vehicle service"
              className="rounded-[2rem] h-72 w-full object-cover shadow-xl sm:mt-10"
            />
          </div>
        </div>
      </section>

      <section className="bg-white py-20 border-y border-slate-200">
        <div className="max-w-7xl mx-auto px-5 md:px-8">
          <div className="text-center max-w-3xl mx-auto mb-12">
            <p className="text-blue-700 font-black uppercase tracking-[0.2em] text-sm">Our Services</p>
            <h3 className="text-4xl md:text-5xl font-black mt-2">Tire Service Delivered To You</h3>
            <p className="text-slate-600 mt-4 text-lg">
              Built for emergency calls, roadside help, daily drivers, commercial trucks, trailers, fleets, big trucks, machines, and OTR tire needs.
            </p>
          </div>
          <div className="grid md:grid-cols-3 gap-6">
            {services.map((item, index) => (
              <div key={item.title} className="group bg-slate-50 border border-slate-200 p-7 rounded-[2rem] shadow-sm hover:shadow-2xl transition duration-300 hover:-translate-y-1">
                <div className="h-14 w-14 rounded-2xl bg-blue-100 text-blue-700 flex items-center justify-center font-black mb-5 group-hover:bg-blue-700 group-hover:text-white transition">
                  {index + 1}
                </div>
                <h3 className="font-black text-xl text-slate-950">{item.title}</h3>
                <p className="text-slate-600 mt-3 leading-relaxed">{item.desc}</p>
              </div>
            ))}
          </div>
        </div>
      </section>

      <section className="relative overflow-hidden bg-slate-950 text-white py-24">
        <div className="absolute inset-0">
          <img
            src="https://images.unsplash.com/photo-1503376780353-7e6692767b70?auto=format&fit=crop&w=1800&q=80"
            alt="Roadside vehicle"
            className="h-full w-full object-cover opacity-25"
          />
        </div>
        <div className="absolute inset-0 bg-gradient-to-r from-slate-950 via-slate-950/90 to-blue-950/70" />
        <div className="relative max-w-7xl mx-auto px-5 md:px-8 grid lg:grid-cols-2 gap-10 items-center">
          <div>
            <p className="text-blue-300 uppercase tracking-[0.2em] font-black text-sm">Why Choose Us</p>
            <h3 className="text-4xl md:text-6xl font-black mt-2 tracking-tight">Professional tire help without the hassle.</h3>
          </div>
          <div className="grid gap-4">
            {[
              'We come to your home, job, yard, job site, or roadside',
              'Mobile truck tire repair available',
              'OTR tire service for machines and big trucks',
              'Fleet and trailer tire support',
              'Commercial-grade mobile equipment',
              'Emergency 24/7 service',
            ].map((item) => (
              <div key={item} className="bg-white/10 border border-white/15 rounded-2xl p-5 backdrop-blur flex items-center gap-4">
                <span className="h-8 w-8 rounded-full bg-blue-500 flex items-center justify-center font-black">✓</span>
                <span className="text-lg font-semibold">{item}</span>
              </div>
            ))}
          </div>
        </div>
      </section>

      <section id="request" className="max-w-7xl mx-auto px-5 md:px-8 py-20">
        <div className="grid lg:grid-cols-[0.9fr_1.1fr] gap-10 items-stretch">
          <div className="bg-gradient-to-br from-blue-700 to-slate-950 text-white rounded-[2rem] p-8 md:p-10 shadow-2xl">
            <p className="text-blue-200 uppercase tracking-[0.2em] font-black text-sm">Request Service</p>
            <h3 className="text-4xl md:text-5xl font-black mt-3">Get help sent to your location.</h3>
            <p className="text-blue-100 mt-5 text-lg">
              For fastest service, text your location, vehicle type, tire size if available, and tire issue.
            </p>
            <div className="mt-8 flex flex-col gap-3">
              <a href={phoneHref} className="bg-white text-blue-700 text-center rounded-2xl py-4 font-black">
                Call {PHONE_DISPLAY}
              </a>
              <a href={smsHref} className="bg-blue-500 text-white text-center rounded-2xl py-4 font-black">
                Text Dispatch
              </a>
            </div>
          </div>
          <div className="bg-white border border-slate-200 p-8 md:p-10 rounded-[2rem] shadow-xl">
            <h3 className="text-3xl font-black">Quick Service Request</h3>
            <p className="text-slate-600 mt-2">Fill this out, then tap send to start a text request.</p>
            <div className="grid md:grid-cols-2 gap-3 mt-6">
              <input className="p-4 rounded-2xl bg-slate-100 border border-slate-200" placeholder="Name" />
              <input className="p-4 rounded-2xl bg-slate-100 border border-slate-200" placeholder="Phone" />
            </div>
            <input className="w-full mt-3 p-4 rounded-2xl bg-slate-100 border border-slate-200" placeholder="Location / Address" />
            <textarea
              className="w-full mt-3 p-4 rounded-2xl bg-slate-100 border border-slate-200"
              placeholder="Tell us what you need: car tire, truck tire, trailer tire, fleet service, machine tire, or OTR tire service"
              rows={5}
            />
            <a href={smsHref} className="block text-center mt-4 w-full bg-blue-700 hover:bg-blue-800 text-white p-4 rounded-2xl font-black shadow-lg shadow-blue-700/20">
              SEND REQUEST
            </a>
          </div>
        </div>
      </section>

      <section className="bg-white py-20 border-y border-slate-200">
        <div className="max-w-7xl mx-auto px-5 md:px-8">
          <div className="flex flex-col md:flex-row md:items-end md:justify-between gap-4 mb-10">
            <div>
              <p className="text-blue-700 uppercase tracking-[0.25em] text-sm font-black">Real Customer Trust</p>
              <h3 className="text-4xl md:text-5xl font-black mt-2">Google Reviews</h3>
              <p className="text-slate-600 mt-3 max-w-2xl">See what customers are saying about Extreme Mobile Tires and Roadside.</p>
            </div>
            <a href={GOOGLE_MAPS_URL} target="_blank" rel="noopener noreferrer" className="bg-green-600 hover:bg-green-700 text-white px-6 py-3 rounded-2xl font-bold text-center">
              View Live Google Reviews
            </a>
          </div>
          <div className="grid md:grid-cols-3 gap-6">
            {reviews.map((review, index) => (
              <div key={`${review.name}-${index}`} className="bg-slate-50 p-7 rounded-[2rem] border border-slate-200 shadow-sm">
                <div className="text-yellow-500 text-xl mb-3">{'★'.repeat(review.rating || 5)}</div>
                <p className="text-slate-700 leading-relaxed">“{review.text}”</p>
                <p className="text-slate-950 font-bold mt-4">{review.name}</p>
                <p className="text-slate-500 text-sm">Google Review</p>
              </div>
            ))}
          </div>
        </div>
      </section>

      <section className="max-w-7xl mx-auto px-5 md:px-8 py-20">
        <div className="grid lg:grid-cols-2 gap-10 items-start">
          <div>
            <p className="text-blue-700 uppercase tracking-[0.25em] text-sm font-black">Questions</p>
            <h3 className="text-4xl md:text-5xl font-black mt-2">Mobile tire service FAQ</h3>
            <p className="text-slate-600 mt-4 text-lg">Quick answers for drivers who need tire help fast.</p>
            <div className="mt-8 bg-blue-700 text-white rounded-3xl p-6 shadow-xl">
              <h4 className="text-2xl font-black">Still need help?</h4>
              <p className="mt-2 text-blue-100">
                Call or text us now for fast dispatch. We handle cars, trucks, trailers, fleets, and OTR equipment.
              </p>
              <div className="mt-4 flex flex-col sm:flex-row gap-3">
                <a href={phoneHref} className="bg-white text-blue-700 px-6 py-3 rounded-2xl font-black text-center">
                  Call {PHONE_DISPLAY}
                </a>
                <a href={smsHref} className="bg-slate-950 text-white px-6 py-3 rounded-2xl font-black text-center">
                  Text Now
                </a>
              </div>
            </div>
          </div>
          <div className="space-y-4">
            {faqs.map((faq) => (
              <div key={faq.q} className="bg-white border border-slate-200 rounded-3xl p-6 shadow-sm">
                <h4 className="font-black text-lg">{faq.q}</h4>
                <p className="text-slate-600 mt-2">{faq.a}</p>
              </div>
            ))}
          </div>
        </div>
      </section>

      <section className="max-w-7xl mx-auto px-5 md:px-8 py-16">
        <div className="bg-white border border-slate-200 rounded-[2rem] p-8 shadow-sm">
          <div className="flex flex-col lg:flex-row lg:items-center lg:justify-between gap-6">
            <div>
              <h3 className="text-4xl font-black">Find Us on Google Maps</h3>
              <p className="text-slate-600 mt-3">Open our Google Maps location, get directions, or leave a review for Extreme Mobile Tires.</p>
            </div>
            <div className="flex flex-wrap gap-4">
              <a href={GOOGLE_MAPS_URL} target="_blank" rel="noopener noreferrer" className="bg-green-600 hover:bg-green-700 text-white px-6 py-4 rounded-2xl font-bold">
                Leave a Review
              </a>
              <a href={GOOGLE_MAPS_URL} target="_blank" rel="noopener noreferrer" className="bg-blue-700 hover:bg-blue-800 text-white px-6 py-4 rounded-2xl font-bold">
                Open Maps
              </a>
              <a href={GOOGLE_MAPS_URL} target="_blank" rel="noopener noreferrer" className="border border-slate-300 text-slate-950 px-6 py-4 rounded-2xl font-bold">
                Directions
              </a>
            </div>
          </div>
        </div>
      </section>

      <section className="bg-gradient-to-br from-blue-700 to-slate-950 text-white py-20">
        <div className="max-w-7xl mx-auto px-5 md:px-8 text-center">
          <h3 className="text-4xl md:text-6xl font-black">Need Tire Help Right Now?</h3>
          <p className="mt-4 text-blue-100 text-lg">
            Call Extreme Mobile Tires and get professional tire, truck tire, trailer tire, fleet tire, or OTR tire help at your location.
          </p>
          <div className="mt-8 flex flex-col sm:flex-row gap-4 justify-center">
            <a href={phoneHref} className="inline-block bg-white text-blue-700 px-10 py-5 rounded-2xl font-black text-xl shadow-xl">
              Call {PHONE_DISPLAY}
            </a>
            <a href={smsHref} className="inline-block bg-blue-500 text-white px-10 py-5 rounded-2xl font-black text-xl shadow-xl">
              Text Now
            </a>
          </div>
        </div>
      </section>

      <section className="max-w-7xl mx-auto px-5 md:px-8 py-20">
        <h3 className="text-4xl font-black mb-6">Service Coverage</h3>
        <div className="grid md:grid-cols-5 gap-3 text-slate-600">
          {coverage.map((item) => (
            <div key={item} className="bg-white border border-slate-200 rounded-2xl p-4 font-semibold text-slate-800 shadow-sm">
              {item}
            </div>
          ))}
        </div>
      </section>

      <footer className="border-t border-slate-200 bg-white py-10 text-center text-slate-500 pb-24 md:pb-10">
        <p className="font-bold text-slate-800">Extreme Mobile Tires</p>
        <p>© 2026 Extreme Mobile Tires | {PHONE_DISPLAY}</p>
      </footer>

      <div className="fixed bottom-0 left-0 right-0 z-40 md:hidden bg-white/95 backdrop-blur border-t border-slate-200 p-3 shadow-2xl">
        <div className="grid grid-cols-2 gap-3">
          <a href={phoneHref} className="bg-blue-700 text-white text-center py-3 rounded-2xl font-black">
            Call Now
          </a>
          <a href={smsHref} className="bg-slate-950 text-white text-center py-3 rounded-2xl font-black">
            Text Now
          </a>
        </div>
      </div>
    </div>
  );
}
