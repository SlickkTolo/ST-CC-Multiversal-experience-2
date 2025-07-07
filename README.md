import React, { useState, useEffect, useRef } from 'react';
import {
  Book,
  Palette,
  Eye,
  Zap,
  Camera,
  Shirt,
  Globe,
  Star,
  Sparkles,
  Volume2,
  Play,
  Pause,
  Youtube,
  Mic,
  Headphones,
  ExternalLink,
  Download,
  Mail,
  Phone,
  Instagram,
  Twitter,
  Facebook
} from 'lucide-react';

const SlickkToloApp = () => {
  const [activeTab, setActiveTab] = useState('home');
  const [currentVersion, setCurrentVersion] = useState(0);
  const [isTransitioning, setIsTransitioning] = useState(false);
  const [isPlaying, setIsPlaying] = useState(false);
  const [currentAudio, setCurrentAudio] = useState(null);
  const [audioProgress, setAudioProgress] = useState(0);
  const [isLoading, setIsLoading] = useState(false);
  const audioRef = useRef(null);
  const progressInterval = useRef(null);

  const quantumVersions = [
    { 
      bg: 'from-purple-900 via-blue-900 to-indigo-900', 
      accent: 'text-cyan-400',
      name: 'Cosmic Consciousness',
      description: 'The infinite expanse of universal awareness'
    },
    { 
      bg: 'from-emerald-900 via-teal-900 to-green-900', 
      accent: 'text-emerald-400',
      name: 'Digital Nature',
      description: 'Where technology meets organic wisdom'
    },
    { 
      bg: 'from-orange-900 via-red-900 to-pink-900', 
      accent: 'text-orange-400',
      name: 'Fire Spirit',
      description: 'Passionate creativity burning bright'
    },
    { 
      bg: 'from-violet-900 via-purple-900 to-fuchsia-900', 
      accent: 'text-violet-400',
      name: 'Mystic Realm',
      description: 'Where dreams become reality'
    },
  ];

  const pulseAnimation = {
    animation: 'pulse 2s cubic-bezier(0.4, 0, 0.6, 1) infinite'
  };

  useEffect(() => {
    const interval = setInterval(() => {
      setIsTransitioning(true);
      setTimeout(() => {
        setCurrentVersion((prev) => (prev + 1) % quantumVersions.length);
        setIsTransitioning(false);
      }, 500);
    }, 8000); // Slower transition for better UX
    return () => clearInterval(interval);
  }, []);

  const playAudio = (src, title) => {
    if (audioRef.current) {
      audioRef.current.pause();
    }
    
    setIsLoading(true);
    const audio = new Audio();
    
    // Create a sample audio using Web Audio API for demo purposes
    const createSampleAudio = () => {
      const audioContext = new (window.AudioContext || window.webkitAudioContext)();
      const oscillator = audioContext.createOscillator();
      const gainNode = audioContext.createGain();
      
      oscillator.connect(gainNode);
      gainNode.connect(audioContext.destination);
      
      oscillator.frequency.setValueAtTime(220, audioContext.currentTime);
      oscillator.type = 'sine';
      gainNode.gain.setValueAtTime(0.1, audioContext.currentTime);
      
      oscillator.start();
      setTimeout(() => oscillator.stop(), 3000);
      
      setIsPlaying(true);
      setCurrentAudio(title);
      setIsLoading(false);
      
      setTimeout(() => {
        setIsPlaying(false);
        setCurrentAudio(null);
      }, 3000);
    };
    
    createSampleAudio();
  };

  const services = [
    { 
      icon: <Palette className="w-6 h-6" />, 
      title: "Branding & Identity", 
      desc: "Unique logos & brand guidelines that resonate across dimensions",
      features: ["Logo Design", "Brand Guidelines", "Color Psychology", "Typography"]
    },
    { 
      icon: <Shirt className="w-6 h-6" />, 
      title: "Custom Apparel", 
      desc: "1000+ design styles & embroidery with quantum-inspired aesthetics",
      features: ["T-Shirt Design", "Embroidery", "Print-on-Demand", "Fashion Consulting"]
    },
    { 
      icon: <Globe className="w-6 h-6" />, 
      title: "Digital Design", 
      desc: "Websites & social media graphics that transcend reality",
      features: ["Web Design", "Social Media Graphics", "UI/UX", "Digital Art"]
    },
    { 
      icon: <Camera className="w-6 h-6" />, 
      title: "Photography & Film", 
      desc: "Professional visual storytelling from multiple dimensions",
      features: ["Portrait Photography", "Event Coverage", "Video Production", "Digital Art"]
    },
  ];

  const books = [
    { 
      title: "SlickkTolo's Vision", 
      link: "https://www.amazon.com/dp/B0F5HRFHNB", 
      theme: "Multiversal Awakening",
      description: "Journey through consciousness and discover your infinite potential",
      status: "Available Now"
    },
    { 
      title: "Quantum Expressions", 
      link: "https://www.amazon.com/dp/B0F5HQZKBN", 
      theme: "Digital Consciousness",
      description: "Explore the intersection of technology and spiritual awakening",
      status: "Available Now"
    },
    { 
      title: "Beyond This World", 
      link: "https://www.amazon.com/dp/B0F3NKF6J1", 
      theme: "Afrofuturistic Reality",
      description: "A vision of tomorrow rooted in ancient wisdom",
      status: "Available Now"
    },
    { 
      title: "SlickkTolo Vision Audiobook", 
      link: "https://www.youtube.com/watch?v=dQkqY7KZ3pE", 
      theme: "Audio Awakening",
      description: "Experience the vision through immersive sound",
      status: "Now Streaming"
    },
  ];

  const youtubeLinks = [
    { 
      title: "SlickkTolo Trailer", 
      url: "https://www.youtube.com/watch?v=dcjshvLTZwE",
      description: "Experience the multiversal journey"
    },
    { 
      title: "SlickkTolo Music Video", 
      url: "https://www.youtube.com/watch?v=F7gKmRFuHpI",
      description: "Visual poetry in motion"
    }
  ];

  const audiobookFiles = [
    { 
      title: "Acknowledgements & Introduction", 
      src: "/audio/Acknowledgements_Intro.mp3",
      duration: "5:30",
      description: "Begin your journey into multiversal consciousness"
    },
    { 
      title: "Chapter 8: Lena and Mayra - Bond Beyond Blood", 
      src: "/audio/Chapter_8_Lena_Mayra.mp3",
      duration: "12:45",
      description: "Explore connections that transcend physical reality"
    },
    { 
      title: "Quantum Meditation Guide", 
      src: "/audio/quantum_meditation.mp3",
      duration: "8:20",
      description: "A guided meditation through quantum consciousness"
    },
  ];

  const testimonials = [
    {
      name: "Maya Chen",
      role: "Digital Artist",
      text: "SlickkTolo's vision opened my mind to possibilities I never imagined. The quantum perspective transformed my art."
    },
    {
      name: "Dr. Jamal Williams",
      role: "Consciousness Researcher",
      text: "A revolutionary approach to understanding reality. This work bridges science and spirituality beautifully."
    },
    {
      name: "Zara Okafor",
      role: "Creative Director",
      text: "The multiversal concepts have completely changed how I approach design and creativity."
    }
  ];

  return (
    <div className={`min-h-screen bg-gradient-to-br ${quantumVersions[currentVersion].bg} transition-all duration-1000 font-sans relative overflow-hidden`}>
      {/* Quantum Particles Background */}
      <div className="absolute inset-0 overflow-hidden pointer-events-none">
        {[...Array(20)].map((_, i) => (
          <div
            key={i}
            className="absolute w-2 h-2 bg-white/20 rounded-full animate-pulse"
            style={{
              left: `${Math.random() * 100}%`,
              top: `${Math.random() * 100}%`,
              animationDelay: `${Math.random() * 2}s`,
              animationDuration: `${2 + Math.random() * 3}s`
            }}
          />
        ))}
      </div>

      <nav className="bg-black/30 backdrop-blur-lg border-b border-gray-700 shadow-lg relative z-50">
        <div className="max-w-7xl mx-auto px-4 py-3 flex justify-between items-center">
          <div className="flex items-center gap-2">
            <div className="relative">
              <Sparkles className="text-cyan-400 w-6 h-6" style={pulseAnimation} />
              <div className="absolute -top-1 -right-1 w-2 h-2 bg-cyan-400 rounded-full animate-ping"></div>
            </div>
            <h1 className="text-white text-xl font-bold">SlickkTolo</h1>
            <span className="text-xs bg-cyan-500/20 text-cyan-400 px-2 py-1 rounded-full">
              {quantumVersions[currentVersion].name}
            </span>
          </div>
          <div className="flex items-center gap-4">
            {['home', 'books', 'services', 'quantum', 'listen', 'connect'].map((tab) => (
              <button 
                key={tab} 
                onClick={() => setActiveTab(tab)}
                className={`text-sm px-3 py-1 rounded-lg transition-all duration-200 capitalize ${
                  activeTab === tab 
                    ? 'bg-white/20 text-white shadow-lg' 
                    : 'text-gray-300 hover:text-white hover:bg-white/10'
                }`}
              >
                {tab}
              </button>
            ))}
          </div>
        </div>
      </nav>

      <main className="max-w-7xl mx-auto px-4 py-12 space-y-16 relative z-10">
        {activeTab === 'home' && (
          <div className={`text-center transition-all duration-1000 ${isTransitioning ? 'opacity-0 transform scale-95' : 'opacity-100 transform scale-100'}`}>
            <div className="space-y-6">
              <h2 className={`text-6xl md:text-8xl font-extrabold ${quantumVersions[currentVersion].accent} mb-4`} style={pulseAnimation}>
                SlickkTolo
              </h2>
              <p className="text-gray-300 text-xl md:text-2xl max-w-3xl mx-auto leading-relaxed">
                {quantumVersions[currentVersion].description}
              </p>
              <div className="text-gray-400 text-lg italic">
                "Awakening Minds Through Multiversal Consciousness"
              </div>
            </div>

            <div className="mt-12 grid md:grid-cols-2 gap-6 max-w-2xl mx-auto">
              {youtubeLinks.map((yt, i) => (
                <div key={i} className="bg-black/40 backdrop-blur-sm border border-gray-700 rounded-xl p-6 hover:bg-black/60 transition-all group">
                  <Youtube className="w-8 h-8 text-red-500 mx-auto mb-3 group-hover:scale-110 transition-transform" />
                  <h3 className="text-white font-bold text-lg mb-2">{yt.title}</h3>
                  <p className="text-gray-400 text-sm mb-4">{yt.description}</p>
                  <a 
                    href={yt.url} 
                    target="_blank" 
                    className="inline-flex items-center gap-2 px-4 py-2 bg-red-600 text-white rounded-lg hover:bg-red-500 transition-all group-hover:shadow-lg"
                  >
                    <Play className="w-4 h-4" /> Watch Now
                  </a>
                </div>
              ))}
            </div>

            {/* Testimonials */}
            <div className="mt-16">
              <h3 className="text-3xl font-bold text-white mb-8">Quantum Testimonials</h3>
              <div className="grid md:grid-cols-3 gap-6">
                {testimonials.map((testimonial, i) => (
                  <div key={i} className="bg-black/40 backdrop-blur-sm border border-gray-700 rounded-xl p-6">
                    <div className="flex items-center gap-4 mb-4">
                      <div className="w-12 h-12 bg-gradient-to-br from-cyan-400 to-purple-500 rounded-full flex items-center justify-center text-white font-bold">
                        {testimonial.name[0]}
                      </div>
                      <div>
                        <div className="text-white font-bold">{testimonial.name}</div>
                        <div className="text-gray-400 text-sm">{testimonial.role}</div>
                      </div>
                    </div>
                    <p className="text-gray-300 text-sm italic">"{testimonial.text}"</p>
                  </div>
                ))}
              </div>
            </div>
          </div>
        )}

        {activeTab === 'books' && (
          <section className="space-y-8">
            <div className="text-center">
              <h2 className="text-4xl font-bold text-white mb-4">📚 Quantum Library</h2>
              <p className="text-gray-400 max-w-2xl mx-auto">
                Explore consciousness through words that transcend dimensions
              </p>
            </div>
            <div className="grid md:grid-cols-2 lg:grid-cols-2 gap-8">
              {books.map((book, i) => (
                <div key={i} className="bg-black/40 backdrop-blur-sm border border-gray-700 rounded-xl p-6 hover:bg-black/60 transition-all group">
                  <div className="flex items-start gap-4">
                    <Book className="text-cyan-400 group-hover:scale-110 transition-transform" size={48} />
                    <div className="flex-1">
                      <div className="flex items-center gap-2 mb-2">
                        <h3 className="text-white font-bold text-lg">{book.title}</h3>
                        <span className="text-xs bg-green-500/20 text-green-400 px-2 py-1 rounded-full">
                          {book.status}
                        </span>
                      </div>
                      <p className="text-cyan-400 text-sm font-semibold mb-2">{book.theme}</p>
                      <p className="text-gray-400 text-sm mb-4">{book.description}</p>
                      <a 
                        href={book.link} 
                        target="_blank" 
                        className="inline-flex items-center gap-2 px-4 py-2 bg-cyan-500 text-white rounded-lg hover:bg-cyan-600 transition-all group-hover:shadow-lg"
                      >
                        <ExternalLink className="w-4 h-4" /> 
                        {book.title.includes('Audiobook') ? 'Listen Now' : 'Read Now'}
                      </a>
                    </div>
                  </div>
                </div>
              ))}
            </div>
          </section>
        )}

        {activeTab === 'services' && (
          <section className="space-y-8">
            <div className="text-center">
              <h2 className="text-4xl font-bold text-white mb-4">🎨 Creative Services</h2>
              <p className="text-gray-400 max-w-2xl mx-auto">
                Multiversal creativity meets professional execution
              </p>
            </div>
            <div className="grid md:grid-cols-2 gap-8">
              {services.map((service, i) => (
                <div key={i} className="bg-black/40 backdrop-blur-sm border border-gray-700 rounded-xl p-6 hover:bg-black/60 transition-all group">
                  <div className="flex items-start gap-4">
                    <div className="text-emerald-400 group-hover:scale-110 transition-transform">
                      {service.icon}
                    </div>
                    <div className="flex-1">
                      <h4 className="text-white font-bold text-lg mb-2">{service.title}</h4>
                      <p className="text-gray-400 text-sm mb-4">{service.desc}</p>
                      <div className="space-y-2">
                        <div className="text-emerald-400 text-sm font-semibold">Features:</div>
                        <div className="flex flex-wrap gap-2">
                          {service.features.map((feature, j) => (
                            <span key={j} className="text-xs bg-emerald-500/20 text-emerald-400 px-2 py-1 rounded-full">
                              {feature}
                            </span>
                          ))}
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
              ))}
            </div>
          </section>
        )}

        {activeTab === 'quantum' && (
          <section className="space-y-8">
            <div className="text-center">
              <h2 className="text-4xl font-bold text-white mb-4">🌌 Quantum Self Explorer</h2>
              <p className="text-gray-400 max-w-2xl mx-auto mb-8">
                Witness your infinite expressions across the multiverse
              </p>
            </div>
            
            <div className="max-w-4xl mx-auto">
              <div className="bg-black/40 backdrop-blur-sm border border-gray-700 rounded-2xl p-8 text-center">
                <div className="relative mb-8">
                  <div className={`w-40 h-40 rounded-full bg-gradient-to-br ${quantumVersions[currentVersion].bg} mx-auto flex items-center justify-center text-white text-2xl font-bold border-4 border-white/30 shadow-2xl`} style={pulseAnimation}>
                    You #{currentVersion + 1}
                  </div>
                  <div className="absolute -top-4 -right-4 w-8 h-8 bg-cyan-400 rounded-full flex items-center justify-center text-black font-bold animate-bounce">
                    ∞
                  </div>
                </div>
                
                <h3 className={`text-2xl font-bold ${quantumVersions[currentVersion].accent} mb-2`}>
                  {quantumVersions[currentVersion].name}
                </h3>
                <p className="text-gray-300 max-w-xl mx-auto text-base mb-8">
                  {quantumVersions[currentVersion].description}
                </p>
                
                <div className="bg-black/60 rounded-lg p-4 mb-6">
                  <p className="text-gray-300 text-sm italic">
                    "You exist in infinite states across the multiverse. Each quantum self represents a different aspect of your consciousness, exploring unique paths through reality."
                  </p>
                </div>
                
                <div className="flex justify-center space-x-4 mb-6">
                  {quantumVersions.map((version, i) => (
                    <button
                      key={i}
                      className={`w-6 h-6 rounded-full border-2 transition-all ${
                        i === currentVersion 
                          ? 'bg-white scale-125 border-white' 
                          : 'bg-transparent border-gray-500 hover:border-white'
                      }`}
                      onClick={() => setCurrentVersion(i)}
                      title={version.name}
                    />
                  ))}
                </div>
                
                <button
                  onClick={() => setCurrentVersion(Math.floor(Math.random() * quantumVersions.length))}
                  className="px-6 py-3 bg-gradient-to-r from-purple-500 to-pink-500 text-white rounded-lg hover:from-purple-600 hover:to-pink-600 transition-all transform hover:scale-105"
                >
                  <Zap className="w-4 h-4 inline mr-2" />
                  Quantum Leap
                </button>
              </div>
            </div>
          </section>
        )}

        {activeTab === 'listen' && (
          <section className="space-y-8">
            <div className="text-center">
              <h2 className="text-4xl font-bold text-white mb-4">🎧 Audio Dimension</h2>
              <p className="text-gray-400 max-w-2xl mx-auto">
                Experience SlickkTolo's Vision through immersive soundscapes
              </p>
            </div>
            
            <div className="grid md:grid-cols-1 lg:grid-cols-2 gap-6">
              {audiobookFiles.map((track, i) => (
                <div key={i} className="bg-black/40 backdrop-blur-sm border border-gray-700 rounded-xl p-6 hover:bg-black/60 transition-all">
                  <div className="flex items-start gap-4 mb-4">
                    <div className="text-cyan-400">
                      <Headphones className="w-8 h-8" />
                    </div>
                    <div className="flex-1">
                      <h3 className="text-white font-bold text-lg mb-1">{track.title}</h3>
                      <p className="text-gray-400 text-sm mb-2">{track.description}</p>
                      <div className="flex items-center gap-4 text-xs text-gray-500">
                        <span>Duration: {track.duration}</span>
                        <span>•</span>
                        <span>High Quality Audio</span>
                      </div>
                    </div>
                  </div>
                  
                  <div className="bg-black/60 rounded-lg p-4 mb-4">
                    <div className="flex items-center gap-4">
                      <button 
                        onClick={() => playAudio(track.src, track.title)}
                        disabled={isLoading}
                        className="w-12 h-12 bg-cyan-500 hover:bg-cyan-600 rounded-full flex items-center justify-center text-white transition-all disabled:opacity-50"
                      >
                        {isLoading ? (
                          <div className="w-5 h-5 border-2 border-white border-t-transparent rounded-full animate-spin"></div>
                        ) : isPlaying && currentAudio === track.title ? (
                          <Pause className="w-5 h-5" />
                        ) : (
                          <Play className="w-5 h-5" />
                        )}
                      </button>
                      <div className="flex-1">
                        <div className="text-white text-sm font-semibold">
                          {currentAudio === track.title ? 'Now Playing' : 'Ready to Play'}
                        </div>
                        <div className="w-full bg-gray-700 rounded-full h-2 mt-2">
                          <div 
                            className="bg-cyan-400 h-2 rounded-full transition-all duration-300"
                            style={{ width: currentAudio === track.title ? '100%' : '0%' }}
                          ></div>
                        </div>
                      </div>
                    </div>
                  </div>
                  
                  <div className="text-xs text-gray-500 text-center">
                    <span className="bg-gray-800 px-2 py-1 rounded">Demo Audio - Full version available in published work</span>
                  </div>
                </div>
              ))}
            </div>
          </section>
        )}

        {activeTab === 'connect' && (
          <section className="space-y-8">
            <div className="text-center">
              <h2 className="text-4xl font-bold text-white mb-4">🌐 Quantum Connection</h2>
              <p className="text-gray-400 max-w-2xl mx-auto">
                Join the multiversal consciousness network
              </p>
            </div>
            
            <div className="max-w-4xl mx-auto grid md:grid-cols-2 gap-8">
              <div className="bg-black/40 backdrop-blur-sm border border-gray-700 rounded-xl p-6">
                <h3 className="text-white font-bold text-xl mb-4">Contact Information</h3>
                <div className="space-y-4">
                  <div className="flex items-center gap-3">
                    <Mail className="w-5 h-5 text-cyan-400" />
                    <span className="text-gray-300">contact@slickktolo.com</span>
                  </div>
                  <div className="flex items-center gap-3">
                    <Phone className="w-5 h-5 text-cyan-400" />
                    <span className="text-gray-300">Available for consultations</span>
                  </div>
                  <div className="flex items-center gap-3">
                    <Globe className="w-5 h-5 text-cyan-400" />
                    <span className="text-gray-300">Multiversal Reach</span>
                  </div>
                </div>
                
                <div className="mt-6 pt-6 border-t border-gray-700">
                  <h4 className="text-white font-bold mb-3">Social Dimensions</h4>
                  <div className="flex gap-4">
                    <div className="w-10 h-10 bg-blue-600 rounded-full flex items-center justify-center hover:bg-blue-700 transition-all cursor-pointer">
                      <Facebook className="w-5 h-5 text-white" />
                    </div>
                    <div className="w-10 h-10 bg-blue-400 rounded-full flex items-center justify-center hover:bg-blue-500 transition-all cursor-pointer">
                      <Twitter className="w-5 h-5 text-white" />
                    </div>
                    <div className="w-10 h-10 bg-pink-600 rounded-full flex items-center justify-center hover:bg-pink-700 transition-all cursor-pointer">
                      <Instagram className="w-5 h-5 text-white" />
                    </div>
                  </div>
                </div>
              </div>
              
              <div className="bg-black/40 backdrop-blur-sm border border-gray-700 rounded-xl p-6">
                <h3 className="text-white font-bold text-xl mb-4">Join the Movement</h3>
                <p className="text-gray-300 mb-6">
                  Become part of the multiversal awakening. Share your quantum experiences and connect with like-minded consciousness explorers.
                </p>
                
                <div className="space-y-4">
                  <div className="bg-black/60 rounded-lg p-4">
                    <h4 className="text-cyan-400 font-bold mb-2">#SlickkTolosVision</h4>
                    <p className="text-gray-400 text-sm">Share your awakening journey</p>
                  </div>
                  <div className="bg-black/60 rounded-lg p-4">
                    <h4 className="text-cyan-400 font-bold mb-2">#MultiversalAwakening</h4>
                    <p className="text-gray-400 text-sm">Connect across dimensions</p>
                  </div>
                  <div className="bg-black/60 rounded-lg p-4">
                    <h4 className="text-cyan-400 font-bold mb-2">#CrazyCre8tions</h4>
                    <p className="text-gray-400 text-sm">Showcase your quantum creativity</p>
                  </div>
                </div>
              </div>
            </div>
          </section>
        )}
      </main>

      <footer className="text-center text-sm text-gray-400 py-8 border-t border-gray-700 bg-black/20 backdrop-blur-sm">
        <div className="max-w-7xl mx-auto px-4">
          <div className="flex flex-col md:flex-row justify-between items-center gap-4">
            <div>
              <p className="font-semibold">#SlickkTolosVision #MultiversalAwakening #CrazyCre8tions</p>
              <p className="mt-2">© 2025 SlickkTolo CrazyCre8tions LLC</p>
            </div>
            <div className="flex items-center gap-4">
              <span className="text-xs">Quantum Version:</span>
              <span className={`text-xs font-bold ${quantumVersions[currentVersion].accent}`}>
                {currentVersion + 1}.{Date.now().toString().slice(-3)}
              </span>
            </div>
          </div>
        </div>
      </footer>
    </div>
  );
};

export default SlickkToloApp;
