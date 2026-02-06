
import React, { useState } from 'react';
import { 
  Instagram, 
  Mail, 
  MessageCircle, 
  Zap, 
  RefreshCw,
  Copy,
  Check,
  Github
} from 'lucide-react';
import { generateFreakQuote } from './services/geminiService';

const TechIcon = ({ name }: { name: string }) => {
  switch (name) {
    case 'JS':
      return <div className="w-12 h-12 bg-yellow-400 text-black flex items-center justify-center font-bold rounded-lg text-xl">JS</div>;
    case 'React':
      return <div className="w-12 h-12 bg-blue-500 text-white flex items-center justify-center font-bold rounded-lg text-2xl">⚛️</div>;
    case 'HTML':
      return <div className="w-12 h-12 bg-orange-600 text-white flex items-center justify-center font-bold rounded-lg text-xl">H5</div>;
    case 'CSS':
      return <div className="w-12 h-12 bg-blue-700 text-white flex items-center justify-center font-bold rounded-lg text-xl">C3</div>;
    default:
      return null;
  }
};

const App: React.FC = () => {
  const [quote, setQuote] = useState("DISCIPLINE OVER EVERYTHING");
  const [isLoadingQuote, setIsLoadingQuote] = useState(false);
  const [copied, setCopied] = useState(false);

  const fetchNewQuote = async () => {
    setIsLoadingQuote(true);
    const newQuote = await generateFreakQuote();
    setQuote(newQuote.toUpperCase());
    setIsLoadingQuote(false);
  };

  const copyReadme = () => {
    const markdown = `<div align="center">

# 🦾 FREAK SEASON
  
<img src="https://readme-typing-svg.herokuapp.com?font=Oswald&weight=700&size=50&pause=1000&color=E11D48&center=true&vCenter=true&width=600&height=100&lines=FREAK+SEASON;${quote.replace(/ /g, '+')};ONLY+THE+STRONG+SURVIVE" alt="Typing SVG" />

### MIGUEL | BIG LOVER OF GANLEY
*Transforming lines of code into lines of muscle.*

---

| 🧱 THE PROCESS | 🔥 THE RESULT |
| :---: | :---: |
| <img src="https://picsum.photos/id/64/400/500?grayscale" width="350" /> | <img src="https://picsum.photos/id/177/400/500?grayscale" width="350" /> |

---

### 🛠️ TECH ARSENAL
<p align="center">
  <img src="https://img.shields.io/badge/javascript-%23323330.svg?style=for-the-badge&logo=javascript&logoColor=%23F7DF1E" />
  <img src="https://img.shields.io/badge/react-%2320232a.svg?style=for-the-badge&logo=react&logoColor=%2361DAFB" />
  <img src="https://img.shields.io/badge/html5-%23E34F26.svg?style=for-the-badge&logo=html5&logoColor=white" />
  <img src="https://img.shields.io/badge/css3-%231572B6.svg?style=for-the-badge&logo=css3&logoColor=white" />
</p>

### 📊 FREAK STATUS
<p align="center">
  <img src="https://img.shields.io/badge/MODE-FREAK-E11D48?style=flat-square&labelColor=18181b" />
  <img src="https://img.shields.io/badge/MINDSET-ALL_DAY-E11D48?style=flat-square&labelColor=18181b" />
  <img src="https://img.shields.io/badge/DISCIPLINE-100%25-E11D48?style=flat-square&labelColor=18181b" />
  <img src="https://img.shields.io/badge/STATUS-ACTIVE-E11D48?style=flat-square&labelColor=18181b" />
</p>

---

### 💬 CURRENT MOTIVATION
> **"${quote}"**

---

### 🔌 CONNECT WITH ME
<p align="center">
  <a href="#"><img src="https://img.shields.io/badge/Instagram-%23E4405F.svg?style=for-the-badge&logo=Instagram&logoColor=white" /></a>
  <a href="#"><img src="https://img.shields.io/badge/Discord-%235865F2.svg?style=for-the-badge&logo=discord&logoColor=white" /></a>
  <a href="#"><img src="https://img.shields.io/badge/Gmail-D14836?style=for-the-badge&logo=gmail&logoColor=white" /></a>
</p>

</div>`;
    
    navigator.clipboard.writeText(markdown);
    setCopied(true);
    setTimeout(() => setCopied(false), 2000);
  };

  return (
    <div className="min-h-screen bg-black text-white checkerboard relative flex flex-col items-center py-10 px-4 md:px-10">
      <div className="absolute inset-0 bg-gradient-to-b from-transparent via-black/50 to-black pointer-events-none"></div>

      <div className="relative z-10 w-full max-w-4xl space-y-12">
        
        {/* Header Section */}
        <header className="w-full bg-zinc-900/80 border-b-4 border-rose-600 p-8 rounded-xl shadow-2xl relative overflow-hidden group">
          <div className="absolute top-0 right-4 top-4">
            <button 
              onClick={copyReadme}
              className="flex items-center gap-2 bg-rose-600 hover:bg-rose-700 text-white text-[10px] font-bold px-3 py-1.5 rounded-full transition-all shadow-lg active:scale-95"
            >
              {copied ? <Check className="w-3 h-3" /> : <Github className="w-3 h-3" />}
              {copied ? 'README COPIED!' : 'GET GITHUB README'}
            </button>
          </div>
          <div className="absolute top-0 left-0 w-full h-1 bg-gradient-to-r from-transparent via-rose-500 to-transparent"></div>
          <div className="text-center space-y-4">
            <h1 className="font-oswald text-6xl md:text-8xl font-black tracking-tighter text-glow animate-pulse">
              FREAK SEASON
            </h1>
            <div className="flex items-center justify-center gap-4 text-zinc-400 font-semibold tracking-widest text-sm md:text-base">
              <span className="h-px w-8 bg-zinc-700"></span>
              MIGUEL | BIG LOVER OF GANLEY
              <span className="h-px w-8 bg-zinc-700"></span>
            </div>
          </div>
        </header>

        {/* Hero Images Grid */}
        <section className="grid grid-cols-1 md:grid-cols-2 gap-8">
          <div className="relative group overflow-hidden rounded-2xl border-2 border-zinc-800 hover:border-rose-600 transition-all duration-500 red-glow">
            <img 
              src="https://picsum.photos/id/64/800/1000?grayscale" 
              alt="The Process" 
              className="w-full h-[400px] object-cover opacity-80 group-hover:scale-105 transition-transform duration-700"
            />
            <div className="absolute inset-0 bg-gradient-to-t from-black via-transparent to-transparent"></div>
            <div className="absolute bottom-6 left-6">
              <span className="font-oswald text-rose-600 font-bold text-xl tracking-tighter drop-shadow-md">THE PROCESS</span>
            </div>
          </div>

          <div className="relative group overflow-hidden rounded-2xl border-2 border-zinc-800 hover:border-rose-600 transition-all duration-500 red-glow">
            <img 
              src="https://picsum.photos/id/177/800/1000?grayscale" 
              alt="The Result" 
              className="w-full h-[400px] object-cover opacity-80 group-hover:scale-105 transition-transform duration-700"
            />
            <div className="absolute inset-0 bg-gradient-to-t from-black via-transparent to-transparent"></div>
            <div className="absolute bottom-6 right-6">
              <span className="font-oswald text-rose-600 font-bold text-xl tracking-tighter drop-shadow-md">THE RESULT</span>
            </div>
          </div>
        </section>

        {/* Motivation Section */}
        <section className="text-center py-6 bg-zinc-900/40 rounded-xl border border-zinc-800 backdrop-blur-sm px-4">
          <div className="flex flex-col items-center gap-4">
            <p className="font-oswald text-3xl md:text-5xl font-black italic tracking-tight">
              {quote.split(" ").map((word, i) => (
                <span key={i} className={['OVER', 'EVERYTHING', 'FREAK', 'STRENGTH'].includes(word) ? 'text-rose-600' : ''}>
                  {word}{" "}
                </span>
              ))}
            </p>
            <button 
              onClick={fetchNewQuote}
              disabled={isLoadingQuote}
              className="flex items-center gap-2 text-zinc-500 hover:text-rose-500 transition-colors text-xs font-bold uppercase tracking-widest mt-2"
            >
              <RefreshCw className={`w-3 h-3 ${isLoadingQuote ? 'animate-spin' : ''}`} />
              {isLoadingQuote ? 'SUMMONING STRENGTH...' : 'GET AI MOTIVATION'}
            </button>
          </div>
        </section>

        {/* Tech Arsenal Section */}
        <section className="flex flex-col items-center gap-6">
          <h3 className="uppercase text-zinc-500 tracking-[0.5em] text-xs font-bold">Tech Arsenal</h3>
          <div className="flex flex-wrap justify-center gap-4">
            {['JS', 'React', 'HTML', 'CSS'].map(tech => (
              <div key={tech} className="p-1 rounded-xl bg-zinc-800/50 border border-zinc-700 hover:border-rose-600 transition-all duration-300">
                <TechIcon name={tech} />
              </div>
            ))}
          </div>
        </section>

        {/* Stats Section */}
        <section className="grid grid-cols-2 md:grid-cols-4 gap-4">
          {[
            { label: 'MODE', value: 'FREAK', color: 'bg-rose-600' },
            { label: 'MINDSET', value: 'ALL DAY', color: 'bg-rose-600' },
            { label: 'DISCIPLINE', value: '100%', color: 'bg-rose-600' },
            { label: 'STATUS', value: 'ACTIVE', color: 'bg-rose-600' }
          ].map((stat, i) => (
            <div key={i} className="flex overflow-hidden rounded-md border border-zinc-800 h-10">
              <div className="bg-zinc-900 px-3 flex items-center justify-center text-[10px] font-black uppercase text-zinc-400 w-1/3">
                {stat.label}
              </div>
              <div className={`${stat.color} px-3 flex items-center justify-center text-[10px] font-black uppercase w-2/3 tracking-widest`}>
                {stat.value}
              </div>
            </div>
          ))}
        </section>

        {/* Social Links Footer */}
        <footer className="flex flex-wrap justify-center gap-4 pt-10 pb-20">
          <a href="#" className="flex items-center gap-2 bg-zinc-900 border border-zinc-800 hover:border-rose-600 px-6 py-3 rounded-md transition-all group">
            <Instagram className="w-5 h-5 text-rose-500 group-hover:scale-110 transition-transform" />
            <span className="text-xs font-bold uppercase tracking-widest">Instagram</span>
          </a>
          <a href="#" className="flex items-center gap-2 bg-zinc-900 border border-zinc-800 hover:border-rose-600 px-6 py-3 rounded-md transition-all group">
            <MessageCircle className="w-5 h-5 text-blue-500 group-hover:scale-110 transition-transform" />
            <span className="text-xs font-bold uppercase tracking-widest">Discord</span>
          </a>
          <a href="#" className="flex items-center gap-2 bg-zinc-900 border border-zinc-800 hover:border-rose-600 px-6 py-3 rounded-md transition-all group">
            <Mail className="w-5 h-5 text-rose-400 group-hover:scale-110 transition-transform" />
            <span className="text-xs font-bold uppercase tracking-widest">Gmail</span>
          </a>
        </footer>
      </div>

      <div className="fixed bottom-6 right-6 z-50">
        <div className="bg-rose-600 p-3 rounded-full shadow-[0_0_20px_rgba(225,29,72,0.8)] animate-bounce cursor-pointer hover:scale-110 transition-transform">
          <Zap className="w-6 h-6 text-white fill-white" />
        </div>
      </div>
    </div>
  );
};

export default App;
