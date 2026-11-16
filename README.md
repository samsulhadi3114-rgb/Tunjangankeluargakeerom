# Tunjangankeluargakeerom
```html
<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>SI TUKEL — Sistem Informasi Tunjangan Keluarga | Pemerintah Kabupaten Keerom</title>
    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Google Fonts: Inter & Plus Jakarta Sans -->
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&family=Plus+Jakarta+Sans:wght@600;700;800&display=swap" rel="stylesheet">
    <!-- Lucide Icons -->
    <script src="https://unpkg.com/lucide@latest"></script>
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    fontFamily: {
                        sans: ['Inter', 'sans-serif'],
                        display: ['Plus Jakarta Sans', 'sans-serif'],
                    },
                    colors: {
                        navy: {
                            800: '#1e3a5f',
                            900: '#0f2544',
                            950: '#09172b',
                        },
                        emerald: {
                            600: '#059669',
                            700: '#047857',
                        },
                        gold: {
                            400: '#fbbf24',
                            500: '#f59e0b',
                        }
                    }
                }
            }
        }
    </script>
    <style>
        ::-webkit-scrollbar { width: 6px; height: 6px; }
        ::-webkit-scrollbar-track { background: #f1f5f9; }
        ::-webkit-scrollbar-thumb { background: #cbd5e1; border-radius: 3px; }
        ::-webkit-scrollbar-thumb:hover { background: #94a3b8; }

        /* Animasi Smooth Accordion untuk Panel Persyaratan */
        .accordion-grid {
            display: grid;
            grid-template-rows: 0fr;
            transition: grid-template-rows 0.35s cubic-bezier(0.4, 0, 0.2, 1);
        }
        .accordion-grid.is-open {
            grid-template-rows: 1fr;
        }
        .accordion-inner {
            overflow: hidden;
        }
    </style>
</head>
<body class="bg-slate-50 text-slate-800 min-h-screen flex flex-col antialiased">

    <!-- Toast Notification Container -->
    <div id="toast-container" class="fixed bottom-5 right-5 z-50 flex flex-col gap-2 max-w-sm w-full pointer-events-none px-4 sm:px-0"></div>

    <!-- Header Resmi Pemerintah Kabupaten Keerom -->
    <header class="bg-navy-900 text-white shadow-lg sticky top-0 z-40 border-b-4 border-emerald-500">
        <div class="max-w-6xl mx-auto px-4 sm:px-6 lg:px-8 py-4">
            <div class="flex flex-col sm:flex-row justify-between items-center gap-3">
                <div class="flex items-center gap-3.5 text-center sm:text-left">
                    <!-- Lambang Resmi Kabupaten Keerom (Inline SVG Presisi) -->
                    <div class="w-14 h-16 flex items-center justify-center shrink-0 drop-shadow-md">
                        <svg viewBox="0 0 320 380" class="w-full h-full" xmlns="http://www.w3.org/2000/svg" role="img" aria-label="Lambang Kabupaten Keerom">
                            <defs>
                                <clipPath id="keerom-shield-clip">
                                    <path d="M 55,10 L 265,10 L 305,46 L 305,195 C 305,270 230,305 160,335 C 90,305 15,270 15,195 L 15,46 Z" />
                                </clipPath>
                                <path id="keerom-ribbon-text-path" d="M 48,325 Q 160,375 272,325" />
                            </defs>

                            <!-- Dasar Perisai -->
                            <g clip-path="url(#keerom-shield-clip)">
                                <!-- Langit Kuning Muda -->
                                <rect x="0" y="54" width="320" height="90" fill="#FCF7C5" />
                                <!-- Gunung Biru -->
                                <path d="M 15,134 Q 55,126 95,112 L 130,98 L 155,95 L 178,84 L 205,98 L 235,114 Q 275,124 305,134 Z" fill="#0088D1" stroke="#1E293B" stroke-width="2" stroke-linejoin="round" />
                                <path d="M 152,96 L 164,114 L 182,118 L 195,105" fill="none" stroke="#1E293B" stroke-width="1.6" stroke-linecap="round" />
                                <path d="M 205,98 L 216,115 L 234,122" fill="none" stroke="#1E293B" stroke-width="1.6" stroke-linecap="round" />
                                <!-- Padang Hijau -->
                                <rect x="0" y="134" width="320" height="210" fill="#7AC143" />
                                <line x1="15" y1="134" x2="305" y2="134" stroke="#1E293B" stroke-width="2" />

                                <!-- Header Kuning Perisai -->
                                <rect x="0" y="0" width="320" height="54" fill="#FACC15" />
                                <line x1="15" y1="54" x2="305" y2="54" stroke="#DC2626" stroke-width="3" />
                                <text x="160" y="42" text-anchor="middle" fill="#111827" font-family="'Plus Jakarta Sans', 'Inter', Arial, sans-serif" font-weight="900" font-size="25" textLength="242" lengthAdjust="spacingAndGlyphs">KABUPATEN KEEROM</text>
                            </g>

                            <!-- Garis Tepi Perisai Merah -->
                            <path d="M 55,10 L 265,10 L 305,46 L 305,195 C 305,270 230,305 160,335 C 90,305 15,270 15,195 L 15,46 Z" fill="none" stroke="#DC2626" stroke-width="4.5" stroke-linejoin="round" />

                            <!-- Tugu Putih di Tengah -->
                            <g stroke="#1E293B" stroke-width="1.5" stroke-linejoin="round">
                                <!-- Undakan Bata Cokelat -->
                                <rect x="115" y="191" width="90" height="8" fill="#D97736" />
                                <line x1="137" y1="191" x2="137" y2="199" />
                                <line x1="160" y1="191" x2="160" y2="199" />
                                <line x1="183" y1="191" x2="183" y2="199" />

                                <rect x="122" y="183" width="76" height="8" fill="#D97736" />
                                <line x1="141" y1="183" x2="141" y2="191" />
                                <line x1="160" y1="183" x2="160" y2="191" />
                                <line x1="179" y1="183" x2="179" y2="191" />

                                <!-- Umpak Putih -->
                                <rect x="131" y="175" width="58" height="8" fill="#FFFFFF" />
                                <line x1="160" y1="175" x2="160" y2="183" />

                                <!-- Badan Tugu Putih -->
                                <polygon points="139,175 149,102 160,100 160,175" fill="#FFFFFF" />
                                <polygon points="160,175 160,100 171,102 181,175" fill="#F1F5F9" />
                            </g>

                            <!-- Tangkai Padi Kuning (Kiri) -->
                            <g stroke="#1E293B" stroke-width="1.3" stroke-linejoin="round">
                                <path d="M 160,262 C 88,255 48,185 88,78" fill="none" stroke="#854D0E" stroke-width="3" stroke-linecap="round" />
                                <!-- Bulir Padi Sisi Luar -->
                                <path d="M 92,76 Q 86,62 98,60 Q 100,72 92,76 Z" fill="#FACC15" />
                                <path d="M 80,96 Q 68,85 78,76 Q 87,86 80,96 Z" fill="#FACC15" />
                                <path d="M 70,118 Q 55,108 64,98 Q 75,108 70,118 Z" fill="#FACC15" />
                                <path d="M 63,142 Q 46,133 54,122 Q 66,131 63,142 Z" fill="#FACC15" />
                                <path d="M 60,166 Q 42,158 49,147 Q 62,155 60,166 Z" fill="#FACC15" />
                                <path d="M 63,190 Q 45,184 51,172 Q 64,179 63,190 Z" fill="#FACC15" />
                                <path d="M 72,213 Q 54,209 59,197 Q 72,202 72,213 Z" fill="#FACC15" />
                                <path d="M 86,233 Q 69,232 73,219 Q 86,223 86,233 Z" fill="#FACC15" />
                                <path d="M 105,249 Q 89,251 92,238 Q 105,240 105,249 Z" fill="#FACC15" />
                                <path d="M 128,259 Q 113,264 114,250 Q 127,250 128,259 Z" fill="#FACC15" />
                                <!-- Bulir Padi Sisi Dalam -->
                                <path d="M 83,95 Q 96,88 100,98 Q 90,104 83,95 Z" fill="#FACC15" />
                                <path d="M 73,117 Q 87,111 91,122 Q 80,127 73,117 Z" fill="#FACC15" />
                                <path d="M 66,141 Q 81,136 84,147 Q 73,151 66,141 Z" fill="#FACC15" />
                                <path d="M 64,165 Q 79,161 81,173 Q 70,176 64,165 Z" fill="#FACC15" />
                                <path d="M 67,189 Q 82,186 83,198 Q 72,200 67,189 Z" fill="#FACC15" />
                                <path d="M 76,211 Q 91,210 91,222 Q 80,223 76,211 Z" fill="#FACC15" />
                                <path d="M 91,231 Q 106,232 104,243 Q 93,242 91,231 Z" fill="#FACC15" />
                                <path d="M 111,246 Q 126,249 122,259 Q 112,257 111,246 Z" fill="#FACC15" />
                            </g>

                            <!-- Tangkai Kapas Putih (Kanan) -->
                            <g stroke="#1E293B" stroke-width="1.3" stroke-linejoin="round">
                                <path d="M 160,262 C 232,255 272,185 224,74" fill="none" stroke="#854D0E" stroke-width="3" stroke-linecap="round" />
                                <!-- Kuntum Kapas 1 (Atas) -->
                                <g transform="translate(222,74)">
                                    <circle cx="-5" cy="-3" r="6" fill="#FFFFFF" />
                                    <circle cx="5" cy="-3" r="6" fill="#FFFFFF" />
                                    <circle cx="0" cy="-7" r="6" fill="#FFFFFF" />
                                    <path d="M -8,1 Q 0,8 8,1 L 4,6 L 0,3 L -4,6 Z" fill="#16A34A" />
                                </g>
                                <!-- Kuntum Kapas 2 -->
                                <g transform="translate(237,96)">
                                    <circle cx="-6" cy="-3" r="6.5" fill="#FFFFFF" />
                                    <circle cx="6" cy="-3" r="6.5" fill="#FFFFFF" />
                                    <circle cx="0" cy="-8" r="6.5" fill="#FFFFFF" />
                                    <path d="M -9,1 Q 0,9 9,1 L 5,7 L 0,4 L -5,7 Z" fill="#16A34A" />
                                </g>
                                <!-- Kuntum Kapas 3 -->
                                <g transform="translate(249,122)">
                                    <circle cx="-6" cy="-3" r="7" fill="#FFFFFF" />
                                    <circle cx="6" cy="-3" r="7" fill="#FFFFFF" />
                                    <circle cx="0" cy="-8" r="7" fill="#FFFFFF" />
                                    <path d="M -10,2 Q 0,10 10,2 L 5,8 L 0,4 L -5,8 Z" fill="#16A34A" />
                                </g>
                                <!-- Kuntum Kapas 4 -->
                                <g transform="translate(256,151)">
                                    <circle cx="-7" cy="-3" r="7.5" fill="#FFFFFF" />
                                    <circle cx="7" cy="-3" r="7.5" fill="#FFFFFF" />
                                    <circle cx="0" cy="-9" r="7.5" fill="#FFFFFF" />
                                    <path d="M -11,2 Q 0,11 11,2 L 6,9 L 0,5 L -6,9 Z" fill="#16A34A" />
                                </g>
                                <!-- Kuntum Kapas 5 -->
                                <g transform="translate(255,182)">
                                    <circle cx="-7" cy="-3" r="8" fill="#FFFFFF" />
                                    <circle cx="7" cy="-3" r="8" fill="#FFFFFF" />
                                    <circle cx="0" cy="-9" r="8" fill="#FFFFFF" />
                                    <path d="M -12,2 Q 0,12 12,2 L 6,9 L 0,5 L -6,9 Z" fill="#16A34A" />
                                </g>
                                <!-- Kuntum Kapas 6 -->
                                <g transform="translate(244,212)">
                                    <circle cx="-7" cy="-3" r="8" fill="#FFFFFF" />
                                    <circle cx="7" cy="-3" r="8" fill="#FFFFFF" />
                                    <circle cx="0" cy="-9" r="8" fill="#FFFFFF" />
                                    <path d="M -12,2 Q 0,12 12,2 L 6,9 L 0,5 L -6,9 Z" fill="#16A34A" />
                                </g>
                                <!-- Kuntum Kapas 7 (Bawah) -->
                                <g transform="translate(222,238)">
                                    <circle cx="-7" cy="-3" r="8.5" fill="#FFFFFF" />
                                    <circle cx="7" cy="-3" r="8.5" fill="#FFFFFF" />
                                    <circle cx="0" cy="-9" r="8.5" fill="#FFFFFF" />
                                    <path d="M -12,2 Q 0,12 12,2 L 6,10 L 0,5 L -6,10 Z" fill="#16A34A" />
                                </g>
                            </g>

                            <!-- Simpul Tali Putih Padi & Kapas -->
                            <g fill="#FFFFFF" stroke="#1E293B" stroke-width="1.4" stroke-linejoin="round">
                                <rect x="150" y="255" width="20" height="9" rx="4" />
                                <path d="M 154,264 C 144,274 152,282 158,272" fill="none" stroke="#FFFFFF" stroke-width="4" stroke-linecap="round" />
                                <path d="M 154,264 C 144,274 152,282 158,272" fill="none" stroke="#1E293B" stroke-width="1.4" stroke-linecap="round" />
                                <path d="M 166,264 C 176,274 168,282 162,272" fill="none" stroke="#FFFFFF" stroke-width="4" stroke-linecap="round" />
                                <path d="M 166,264 C 176,274 168,282 162,272" fill="none" stroke="#1E293B" stroke-width="1.4" stroke-linecap="round" />
                            </g>

                            <!-- Dua Tifa Bersilangan di Bagian Bawah -->
                            <!-- Tifa Kiri (Mengarah Kanan Bawah) -->
                            <g transform="translate(112, 282) rotate(26)" stroke="#1E293B" stroke-width="1.4" stroke-linejoin="round">
                                <path d="M -45,-12 L 22,-8 L 22,8 L -45,12 Z" fill="#A14A24" />
                                <ellipse cx="-45" cy="0" rx="5" ry="12" fill="#E2E8F0" />
                                <polygon points="-36,-7 -24,-1 -36,6" fill="#FFFFFF" />
                                <path d="M -18,-6 L -12,6 M -10,-6 L -4,6" stroke="#FFFFFF" stroke-width="2" />
                                <path d="M 2,-4 Q 8,-7 12,-2 Q 15,3 8,5 Q 3,6 5,1" fill="none" stroke="#FFFFFF" stroke-width="2" stroke-linecap="round" />
                                <rect x="22" y="-6" width="12" height="12" rx="2" fill="#94A3B8" />
                                <rect x="34" y="-4" width="16" height="8" rx="3" fill="#FFFFFF" />
                            </g>

                            <!-- Tifa Kanan (Mengarah Kiri Bawah) -->
                            <g transform="translate(208, 282) rotate(-26)" stroke="#1E293B" stroke-width="1.4" stroke-linejoin="round">
                                <path d="M 45,-12 L -22,-8 L -22,8 L 45,12 Z" fill="#A14A24" />
                                <ellipse cx="45" cy="0" rx="5" ry="12" fill="#E2E8F0" />
                                <polygon points="36,-8 18,0 36,8" fill="none" stroke="#FFFFFF" stroke-width="2.2" />
                                <path d="M 10,-4 Q 4,-7 0,-2 Q -3,3 4,5" fill="none" stroke="#FFFFFF" stroke-width="2" stroke-linecap="round" />
                                <path d="M -6,-4 Q -12,-7 -16,-2 Q -19,3 -12,5" fill="none" stroke="#FFFFFF" stroke-width="2" stroke-linecap="round" />
                                <rect x="-34" y="-6" width="12" height="12" rx="2" fill="#94A3B8" />
                                <rect x="-50" y="-4" width="16" height="8" rx="3" fill="#FFFFFF" />
                            </g>

                            <!-- Pita Semboyan "TAMNE YISAN KEFASE" -->
                            <g stroke="#DC2626" stroke-width="2.5" stroke-linejoin="round">
                                <path d="M 55,315 L 18,282 L 26,312 L 15,326 L 45,342 L 58,332 Z" fill="#FACC15" />
                                <path d="M 265,315 L 302,282 L 294,312 L 305,326 L 275,342 L 262,332 Z" fill="#FACC15" />
                                <path d="M 42,302 Q 160,352 278,302 L 270,336 Q 160,384 50,336 Z" fill="#FACC15" />
                            </g>

                            <!-- Teks Semboyan Melengkung pada Pita -->
                            <text fill="#1E1B4B" font-family="'Plus Jakarta Sans', 'Inter', Arial, sans-serif" font-weight="900" font-size="19.5" letter-spacing="1.2">
                                <textPath href="#keerom-ribbon-text-path" startOffset="50%" text-anchor="middle">TAMNE YISAN KEFASE</textPath>
                            </text>
                        </svg>
                    </div>
                    <div>
                        <p class="text-[11px] font-bold uppercase tracking-widest text-gold-400">Pemerintah Kabupaten Keerom</p>
                        <h1 class="font-display font-extrabold text-lg sm:text-xl tracking-tight text-white leading-snug">
                            SI TUKEL <span class="font-normal text-slate-300 hidden md:inline">— Sistem Informasi Tunjangan Keluarga</span>
                        </h1>
                        <p class="text-xs text-slate-300 md:hidden">Sistem Informasi Tunjangan Keluarga</p>
                    </div>
                </div>

                <!-- Badge Layanan Mandiri -->
                <div class="inline-flex items-center gap-2 px-3.5 py-1.5 rounded-full bg-white/10 border border-white/15 text-xs font-medium text-emerald-300">
                    <span class="w-2 h-2 rounded-full bg-emerald-400 animate-pulse"></span>
                    <span>Layanan Cek & Simulasi Mandiri ASN</span>
                </div>
            </div>
        </div>
    </header>

    <!-- Main Content -->
    <main class="flex-grow max-w-6xl w-full mx-auto px-4 sm:px-6 lg:px-8 py-6 sm:py-8 space-y-6">

        <!-- Hero Info Ringkas -->
        <div class="bg-white rounded-2xl p-5 sm:p-6 shadow-xs border border-slate-200/80 flex flex-col md:flex-row items-start md:items-center justify-between gap-4">
            <div class="space-y-1">
                <h2 class="font-display font-bold text-lg sm:text-xl text-navy-900">Kalkulator & Informasi Besaran Tunjangan Keluarga</h2>
                <p class="text-xs sm:text-sm text-slate-600 leading-relaxed max-w-3xl">
                    Hitung estimasi nominal <strong>Tunjangan Suami/Istri (10%)</strong> dan <strong>Tunjangan Anak (2% per anak)</strong> secara mandiri dan instan berdasarkan Gaji Pokok ASN. Klik tombol persyaratan di bawah untuk melihat kelengkapan berkas.
                </p>
            </div>
            <div class="flex flex-wrap items-center gap-2 shrink-0">
                <button type="button" onclick="togglePersyaratan(true)" class="inline-flex items-center gap-2 px-4 py-2.5 rounded-xl bg-navy-900 hover:bg-navy-800 text-white text-xs font-semibold shadow-xs transition cursor-pointer">
                    <i data-lucide="file-check-2" class="w-4 h-4 text-gold-400"></i>
                    <span>Cek Persyaratan</span>
                </button>
                <button type="button" onclick="scrollToRegulasi()" class="inline-flex items-center gap-2 px-4 py-2.5 rounded-xl bg-slate-100 hover:bg-slate-200/80 text-navy-900 text-xs font-semibold transition cursor-pointer">
                    <i data-lucide="book-open-check" class="w-4 h-4 text-emerald-600"></i>
                    <span>Dasar Regulasi</span>
                </button>
            </div>
        </div>

        <!-- Panel Interaktif (Accordion): Persyaratan Pengajuan Tunjangan Keluarga -->
        <section id="panel-persyaratan" class="bg-white rounded-2xl shadow-sm border border-slate-200/80 overflow-hidden transition-all">
            <!-- Tombol Trigger Header Accordion (Dapat Diklik) -->
            <button type="button" id="btn-toggle-persyaratan" onclick="togglePersyaratan()" aria-expanded="false" aria-controls="persyaratan-accordion-body" class="w-full px-5 sm:px-6 py-4 bg-gradient-to-r from-navy-900 via-navy-800 to-navy-900 hover:from-navy-800 hover:to-navy-900 text-white flex items-center justify-between gap-4 text-left transition cursor-pointer group">
                <div class="flex items-center gap-3.5">
                    <div class="w-10 h-10 rounded-xl bg-white/10 border border-white/15 text-gold-400 flex items-center justify-center shrink-0 group-hover:scale-105 transition-transform">
                        <i data-lucide="clipboard-list" class="w-5 h-5"></i>
                    </div>
                    <div>
                        <div class="flex flex-wrap items-center gap-2">
                            <h3 class="font-display font-bold text-sm sm:text-base md:text-lg text-white">Persyaratan Pengajuan Tunjangan Keluarga</h3>
                            <span id="badge-status-persyaratan" class="inline-flex items-center gap-1 text-[11px] font-bold px-2.5 py-0.5 rounded-full bg-emerald-500/20 text-emerald-300 border border-emerald-400/30 transition-colors">
                                Klik untuk Lihat Persyaratan
                            </span>
                        </div>
                        <p class="text-xs text-slate-300 mt-0.5">Daftar kelengkapan administrasi pengajuan Tunjangan Suami/Istri (10%) & Tunjangan Anak (2%)</p>
                    </div>
                </div>

                <!-- Tombol Aksi & Ikon Panah Berputar -->
                <div class="flex items-center gap-2.5 shrink-0">
                    <span id="label-toggle-persyaratan" class="hidden sm:inline-block text-xs font-semibold text-gold-400 group-hover:underline">
                        Klik untuk Lihat Persyaratan
                    </span>
                    <div class="w-9 h-9 rounded-xl bg-white/10 border border-white/15 flex items-center justify-center shrink-0 group-hover:bg-white/20 transition">
                        <i id="icon-chevron-persyaratan" data-lucide="chevron-down" class="w-5 h-5 text-gold-400 transition-transform duration-300"></i>
                    </div>
                </div>
            </button>

            <!-- Konten Collapsible Accordion -->
            <div id="persyaratan-accordion-body" class="accordion-grid">
                <div class="accordion-inner">
                    <div class="p-5 sm:p-6 space-y-5 border-t border-slate-200/80 bg-white">
                        <div class="grid grid-cols-1 md:grid-cols-2 gap-5">
                            <!-- Kartu Syarat Tunjangan Suami/Istri -->
                            <div class="rounded-xl border border-slate-200/90 bg-slate-50/70 p-5 flex flex-col justify-between space-y-4">
                                <div class="space-y-3">
                                    <div class="flex items-center justify-between gap-2 pb-3 border-b border-slate-200/80">
                                        <div class="flex items-center gap-2.5">
                                            <div class="w-8 h-8 rounded-lg bg-navy-900 text-white flex items-center justify-center shrink-0">
                                                <i data-lucide="heart-handshake" class="w-4 h-4 text-gold-400"></i>
                                            </div>
                                            <h4 class="font-display font-bold text-sm sm:text-base text-navy-900">1. Tunjangan Suami / Istri (10%)</h4>
                                        </div>
                                        <span class="text-[11px] font-bold px-2.5 py-0.5 rounded-md bg-navy-900/10 text-navy-900 shrink-0">10% Gapok</span>
                                    </div>

                                    <ul class="space-y-2.5 text-xs sm:text-sm text-slate-700">
                                        <li class="flex items-start gap-2.5">
                                            <i data-lucide="check-circle-2" class="w-4 h-4 text-emerald-600 shrink-0 mt-0.5"></i>
                                            <span>Surat permohonan / pengantar pengajuan tunjangan keluarga dari unit kerja.</span>
                                        </li>
                                        <li class="flex items-start gap-2.5">
                                            <i data-lucide="check-circle-2" class="w-4 h-4 text-emerald-600 shrink-0 mt-0.5"></i>
                                            <span>Fotokopi sah <strong>Buku Nikah / Akta Perkawinan</strong> yang diterbitkan oleh KUA atau Dinas Dukcapil (dilegalisir).</span>
                                        </li>
                                        <li class="flex items-start gap-2.5">
                                            <i data-lucide="check-circle-2" class="w-4 h-4 text-emerald-600 shrink-0 mt-0.5"></i>
                                            <span>Fotokopi <strong>Kartu Keluarga (KK)</strong> terbaru yang telah memuat nama suami dan istri.</span>
                                        </li>
                                        <li class="flex items-start gap-2.5">
                                            <i data-lucide="check-circle-2" class="w-4 h-4 text-emerald-600 shrink-0 mt-0.5"></i>
                                            <span>Fotokopi <strong>SK CPNS / SK PNS / SK PPPK</strong> dan SK Pangkat/Berkala terakhir.</span>
                                        </li>
                                        <li class="flex items-start gap-2.5">
                                            <i data-lucide="check-circle-2" class="w-4 h-4 text-emerald-600 shrink-0 mt-0.5"></i>
                                            <span><strong>Surat Keterangan Tidak Menerima Tunjangan Keluarga Ganda</strong> (apabila pasangan juga berstatus ASN/TNI/Polri, tunjangan diberikan pada gaji pokok tertinggi).</span>
                                        </li>
                                    </ul>
                                </div>
                            </div>

                            <!-- Kartu Syarat Tunjangan Anak -->
                            <div class="rounded-xl border border-slate-200/90 bg-slate-50/70 p-5 flex flex-col justify-between space-y-4">
                                <div class="space-y-3">
                                    <div class="flex items-center justify-between gap-2 pb-3 border-b border-slate-200/80">
                                        <div class="flex items-center gap-2.5">
                                            <div class="w-8 h-8 rounded-lg bg-emerald-700 text-white flex items-center justify-center shrink-0">
                                                <i data-lucide="baby" class="w-4 h-4 text-white"></i>
                                            </div>
                                            <h4 class="font-display font-bold text-sm sm:text-base text-navy-900">2. Tunjangan Anak (Maks. 2 Anak)</h4>
                                        </div>
                                        <span class="text-[11px] font-bold px-2.5 py-0.5 rounded-md bg-emerald-100 text-emerald-800 shrink-0">2% / Anak</span>
                                    </div>

                                    <ul class="space-y-2.5 text-xs sm:text-sm text-slate-700">
                                        <li class="flex items-start gap-2.5">
                                            <i data-lucide="check-circle-2" class="w-4 h-4 text-emerald-600 shrink-0 mt-0.5"></i>
                                            <span>Fotokopi sah <strong>Akta Kelahiran Anak</strong> dari Dinas Kependudukan dan Pencatatan Sipil (Dukcapil).</span>
                                        </li>
                                        <li class="flex items-start gap-2.5">
                                            <i data-lucide="check-circle-2" class="w-4 h-4 text-emerald-600 shrink-0 mt-0.5"></i>
                                            <span>Fotokopi <strong>Kartu Keluarga (KK)</strong> terbaru yang telah mencantumkan NIK dan nama anak.</span>
                                        </li>
                                        <li class="flex items-start gap-2.5">
                                            <i data-lucide="check-circle-2" class="w-4 h-4 text-emerald-600 shrink-0 mt-0.5"></i>
                                            <span>Berusia di bawah <strong>21 tahun</strong>, belum pernah menikah, dan belum mempunyai penghasilan sendiri.</span>
                                        </li>
                                        <li class="flex items-start gap-2.5">
                                            <i data-lucide="check-circle-2" class="w-4 h-4 text-emerald-600 shrink-0 mt-0.5"></i>
                                            <span><strong>Surat Keterangan Masih Sekolah / Kuliah Asli</strong> (wajib dilampirkan bagi anak berusia <strong>21 s.d. 25 tahun</strong> yang masih menempuh pendidikan).</span>
                                        </li>
                                        <li class="flex items-start gap-2.5">
                                            <i data-lucide="check-circle-2" class="w-4 h-4 text-emerald-600 shrink-0 mt-0.5"></i>
                                            <span>Khusus anak angkat/tiri: melampirkan salinan <strong>Penetapan Pengadilan</strong> (anak angkat) atau akta nikah/cerai/kematian yang sah (anak tiri).</span>
                                        </li>
                                    </ul>
                                </div>
                            </div>
                        </div>

                        <!-- Catatan Penting & Tombol Tutup Panel -->
                        <div class="flex flex-col sm:flex-row items-start sm:items-center justify-between gap-3 p-3.5 rounded-xl bg-navy-900/5 border border-navy-900/15 text-xs text-slate-700">
                            <div class="flex items-start gap-3">
                                <i data-lucide="info" class="w-4 h-4 text-navy-800 shrink-0 mt-0.5"></i>
                                <p class="leading-relaxed">
                                    <strong>Catatan Pelaporan:</strong> Berkas fisik diserahkan ke Subbagian Umum & Kepegawaian OPD untuk pemutakhiran daftar gaji.
                                </p>
                            </div>
                            <button type="button" onclick="togglePersyaratan(false)" class="self-end sm:self-center shrink-0 inline-flex items-center gap-1.5 px-3 py-1.5 rounded-lg bg-white hover:bg-slate-100 border border-slate-300 text-navy-900 font-semibold text-xs transition cursor-pointer">
                                <i data-lucide="chevron-up" class="w-3.5 h-3.5"></i>
                                <span>Tutup Persyaratan</span>
                            </button>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- Grid Utama: Kalkulator Input (Kiri) & Hasil Rincian Real-Time (Kanan) -->
        <div id="panel-kalkulator" class="grid grid-cols-1 lg:grid-cols-12 gap-6 items-start">

            <!-- KOLOM KIRI (7 Kolom): Parameter Perhitungan -->
            <div class="lg:col-span-7 bg-white rounded-2xl shadow-sm border border-slate-200/80 p-6 sm:p-7 space-y-6">
                <div class="flex items-center justify-between border-b border-slate-100 pb-4">
                    <div>
                        <h3 class="font-display font-bold text-base sm:text-lg text-navy-900">Parameter Data Gaji & Keluarga</h3>
                        <p class="text-xs text-slate-500">Pilih golongan atau masukkan nominal Gaji Pokok Anda secara langsung.</p>
                    </div>
                    <button type="button" onclick="resetKalkulator()" class="inline-flex items-center gap-1.5 text-xs font-semibold text-slate-500 hover:text-navy-900 px-3 py-1.5 rounded-lg hover:bg-slate-100 transition cursor-pointer">
                        <i data-lucide="rotate-ccw" class="w-3.5 h-3.5"></i>
                        <span>Reset</span>
                    </button>
                </div>

                <!-- 1. Identitas Opsional (Untuk Label Riwayat Simulasi) -->
                <div class="grid grid-cols-1 sm:grid-cols-2 gap-4 bg-slate-50/80 p-4 rounded-xl border border-slate-200/70">
                    <div>
                        <label for="inp-nama" class="block text-xs font-semibold text-slate-700 mb-1">Nama Pegawai <span class="font-normal text-slate-400">(Opsional)</span></label>
                        <input type="text" id="inp-nama" placeholder="Contoh: Yohanes Wenda, S.Sos" class="w-full px-3.5 py-2 rounded-xl border border-slate-300 bg-white focus:border-emerald-600 focus:ring-2 focus:ring-emerald-600/20 outline-none text-sm transition">
                    </div>
                    <div>
                        <label for="inp-nip" class="block text-xs font-semibold text-slate-700 mb-1">NIP <span class="font-normal text-slate-400">(Opsional)</span></label>
                        <input type="text" id="inp-nip" placeholder="Contoh: 199205142025041002" maxlength="21" class="w-full px-3.5 py-2 rounded-xl border border-slate-300 bg-white focus:border-emerald-600 focus:ring-2 focus:ring-emerald-600/20 outline-none text-sm font-mono transition">
                    </div>
                </div>

                <!-- 2. Pemilihan Golongan / Nominal Gaji Pokok -->
                <div class="space-y-3">
                    <label for="inp-golongan" class="block text-xs font-bold text-slate-700">Referensi Golongan / Ruang (PP No. 5 Tahun 2024)</label>
                    <select id="inp-golongan" onchange="handleGolonganChange()" class="w-full px-3.5 py-2.5 rounded-xl border border-slate-300 bg-white focus:border-emerald-600 focus:ring-2 focus:ring-emerald-600/20 outline-none text-sm font-medium transition">
                        <option value="custom">-- Input Nominal Gaji Pokok Manual --</option>
                        <optgroup label="Golongan I (Juru)">
                            <option value="1685700|Golongan I.a (MKG 0 Thn)">Golongan I.a (MKG 0 Tahun) — Rp 1.685.700</option>
                            <option value="1840800|Golongan I.b (MKG 3 Thn)">Golongan I.b (MKG 3 Tahun) — Rp 1.840.800</option>
                            <option value="1918700|Golongan I.c (MKG 3 Thn)">Golongan I.c (MKG 3 Tahun) — Rp 1.918.700</option>
                            <option value="1999900|Golongan I.d (MKG 3 Thn)">Golongan I.d (MKG 3 Tahun) — Rp 1.999.900</option>
                        </optgroup>
                        <optgroup label="Golongan II (Pengatur)">
                            <option value="2184000|Golongan II.a (MKG 0 Thn)">Golongan II.a (MKG 0 Tahun) — Rp 2.184.000</option>
                            <option value="2385000|Golongan II.b (MKG 3 Thn)">Golongan II.b (MKG 3 Tahun) — Rp 2.385.000</option>
                            <option value="2485900|Golongan II.c (MKG 3 Thn)">Golongan II.c (MKG 3 Tahun) — Rp 2.485.900</option>
                            <option value="2591100|Golongan II.d (MKG 3 Thn)">Golongan II.d (MKG 3 Tahun) — Rp 2.591.100</option>
                        </optgroup>
                        <optgroup label="Golongan III (Penata)">
                            <option value="2785700|Golongan III.a (MKG 0 Thn)" selected>Golongan III.a (MKG 0 Tahun) — Rp 2.785.700</option>
                            <option value="2903600|Golongan III.b (MKG 0 Thn)">Golongan III.b (MKG 0 Tahun) — Rp 2.903.600</option>
                            <option value="3026400|Golongan III.c (MKG 0 Thn)">Golongan III.c (MKG 0 Tahun) — Rp 3.026.400</option>
                            <option value="3154400|Golongan III.d (MKG 0 Thn)">Golongan III.d (MKG 0 Tahun) — Rp 3.154.400</option>
                        </optgroup>
                        <optgroup label="Golongan IV (Pembina)">
                            <option value="3287800|Golongan IV.a (MKG 0 Thn)">Golongan IV.a (MKG 0 Tahun) — Rp 3.287.800</option>
                            <option value="3426900|Golongan IV.b (MKG 0 Thn)">Golongan IV.b (MKG 0 Tahun) — Rp 3.426.900</option>
                            <option value="3571900|Golongan IV.c (MKG 0 Thn)">Golongan IV.c (MKG 0 Tahun) — Rp 3.571.900</option>
                            <option value="3723000|Golongan IV.d (MKG 0 Thn)">Golongan IV.d (MKG 0 Tahun) — Rp 3.723.000</option>
                            <option value="3880400|Golongan IV.e (MKG 0 Thn)">Golongan IV.e (MKG 0 Tahun) — Rp 3.880.400</option>
                        </optgroup>
                    </select>

                    <div>
                        <label for="inp-gapok" class="block text-xs font-bold text-slate-700 mb-1.5">Nominal Gaji Pokok (GAPOK) Sesuai Daftar Gaji / SK Terakhir <span class="text-rose-500">*</span></label>
                        <div class="relative">
                            <span class="absolute left-3.5 top-1/2 -translate-y-1/2 text-sm font-bold text-slate-500">Rp</span>
                            <input type="text" id="inp-gapok" value="2.785.700" oninput="handleManualGapok(this)" class="w-full pl-10 pr-4 py-3 rounded-xl border-2 border-slate-300 focus:border-emerald-600 focus:ring-2 focus:ring-emerald-600/20 outline-none text-base font-bold text-navy-900 transition">
                        </div>
                        <p class="text-[11px] text-slate-500 mt-1">Anda dapat mengubah langsung angka di atas sesuai nominal Gaji Pokok pada KGB / SK Pangkat terakhir.</p>
                    </div>
                </div>

                <!-- 3. Status Tunjangan Suami/Istri -->
                <div>
                    <label class="block text-xs font-bold text-slate-700 mb-2">Status Tunjangan Suami / Istri (10% dari Gaji Pokok)</label>
                    <div class="grid grid-cols-1 sm:grid-cols-2 gap-3">
                        <label class="cursor-pointer">
                            <input type="radio" name="status_nikah" value="0" onchange="hitungTunjangan()" class="peer hidden">
                            <div class="p-3.5 rounded-xl border-2 border-slate-200 bg-white peer-checked:border-navy-900 peer-checked:bg-navy-900/5 transition flex items-center justify-between">
                                <div class="flex items-center gap-2.5">
                                    <div class="w-8 h-8 rounded-lg bg-slate-100 text-slate-600 flex items-center justify-center">
                                        <i data-lucide="user" class="w-4 h-4"></i>
                                    </div>
                                    <div>
                                        <p class="text-xs font-bold text-slate-800">Belum Menikah / Lajang</p>
                                        <p class="text-[11px] text-slate-500">Tanpa tunjangan pasangan</p>
                                    </div>
                                </div>
                                <span class="text-xs font-bold px-2 py-0.5 rounded-md bg-slate-100 text-slate-600">0%</span>
                            </div>
                        </label>

                        <label class="cursor-pointer">
                            <input type="radio" name="status_nikah" value="0.10" onchange="hitungTunjangan()" checked class="peer hidden">
                            <div class="p-3.5 rounded-xl border-2 border-slate-200 bg-white peer-checked:border-emerald-600 peer-checked:bg-emerald-50/60 transition flex items-center justify-between">
                                <div class="flex items-center gap-2.5">
                                    <div class="w-8 h-8 rounded-lg bg-emerald-100 text-emerald-700 flex items-center justify-center">
                                        <i data-lucide="users" class="w-4 h-4"></i>
                                    </div>
                                    <div>
                                        <p class="text-xs font-bold text-slate-800">Menikah (Suami / Istri)</p>
                                        <p class="text-[11px] text-slate-500">10% dari Gaji Pokok</p>
                                    </div>
                                </div>
                                <span class="text-xs font-extrabold px-2 py-0.5 rounded-md bg-emerald-600 text-white">10%</span>
                            </div>
                        </label>
                    </div>
                </div>

                <!-- 4. Jumlah Anak Tertanggung -->
                <div>
                    <div class="flex items-center justify-between mb-2">
                        <label class="block text-xs font-bold text-slate-700">Jumlah Anak Tertanggung (Maksimal 2 Anak)</label>
                        <span class="text-[11px] font-semibold text-emerald-700 bg-emerald-50 px-2 py-0.5 rounded-md border border-emerald-200">2% per anak</span>
                    </div>
                    <div class="grid grid-cols-3 gap-3">
                        <label class="cursor-pointer">
                            <input type="radio" name="jumlah_anak" value="0" onchange="hitungTunjangan()" class="peer hidden">
                            <div class="p-3 rounded-xl border-2 border-slate-200 bg-white peer-checked:border-navy-900 peer-checked:bg-navy-900/5 text-center transition">
                                <p class="font-display font-bold text-sm text-slate-800">0 Anak</p>
                                <p class="text-[11px] text-slate-500 mt-0.5">0%</p>
                            </div>
                        </label>

                        <label class="cursor-pointer">
                            <input type="radio" name="jumlah_anak" value="1" onchange="hitungTunjangan()" checked class="peer hidden">
                            <div class="p-3 rounded-xl border-2 border-slate-200 bg-white peer-checked:border-emerald-600 peer-checked:bg-emerald-50/60 text-center transition">
                                <p class="font-display font-bold text-sm text-slate-800">1 Anak</p>
                                <p class="text-[11px] font-semibold text-emerald-700 mt-0.5">+2% Gapok</p>
                            </div>
                        </label>

                        <label class="cursor-pointer">
                            <input type="radio" name="jumlah_anak" value="2" onchange="hitungTunjangan()" class="peer hidden">
                            <div class="p-3 rounded-xl border-2 border-slate-200 bg-white peer-checked:border-emerald-600 peer-checked:bg-emerald-50/60 text-center transition">
                                <p class="font-display font-bold text-sm text-slate-800">2 Anak</p>
                                <p class="text-[11px] font-semibold text-emerald-700 mt-0.5">+4% Gapok</p>
                            </div>
                        </label>
                    </div>

                    <!-- Catatan Informatif Batas Usia Anak -->
                    <div class="mt-3 p-3 rounded-xl bg-amber-50/80 border border-amber-200/80 flex items-start gap-2.5 text-xs text-amber-900">
                        <i data-lucide="info" class="w-4 h-4 text-amber-600 shrink-0 mt-0.5"></i>
                        <p class="leading-relaxed">
                            <strong>Ketentuan Anak Tertanggung:</strong> Maksimal 2 (dua) orang anak dengan batas usia <strong>21 tahun</strong>, belum pernah menikah, dan belum berpenghasilan sendiri. Batas usia dapat diperpanjang hingga <strong>25 tahun</strong> apabila anak masih bersekolah/kuliah (dibuktikan Surat Keterangan Kuliah).
                        </p>
                    </div>
                </div>
            </div>

            <!-- KOLOM KANAN (5 Kolom): Kartu Hasil Rincian Real-Time -->
            <div class="lg:col-span-5 space-y-5 lg:sticky lg:top-24">
                <div class="bg-gradient-to-br from-navy-900 via-navy-800 to-navy-950 text-white rounded-2xl shadow-xl border border-navy-700 overflow-hidden">
                    <!-- Header Kartu Hasil -->
                    <div class="px-6 py-4 bg-white/5 border-b border-white/10 flex items-center justify-between">
                        <div class="flex items-center gap-2">
                            <i data-lucide="calculator" class="w-4 h-4 text-gold-400"></i>
                            <span class="text-xs font-bold uppercase tracking-wider text-gold-400">Rincian Estimasi Bulanan</span>
                        </div>
                        <span id="badge-total-persen" class="text-[11px] font-bold px-2.5 py-0.5 rounded-full bg-emerald-500/20 text-emerald-300 border border-emerald-400/30">
                            Tunjangan +12%
                        </span>
                    </div>

                    <!-- Isi Rincian Angka -->
                    <div class="p-6 space-y-4">
                        <!-- Gaji Pokok -->
                        <div class="flex justify-between items-center text-sm">
                            <span class="text-slate-300">Gaji Pokok Dasar</span>
                            <span id="res-gapok" class="font-semibold text-white">Rp 2.785.700</span>
                        </div>

                        <hr class="border-white/10">

                        <!-- Tunjangan Suami/Istri -->
                        <div class="flex justify-between items-center text-sm">
                            <div>
                                <span class="text-slate-200 block">Tunjangan Suami / Istri</span>
                                <span id="res-nikah-label" class="text-[11px] text-emerald-400">10% × Gaji Pokok</span>
                            </div>
                            <span id="res-tunj-nikah" class="font-semibold text-emerald-300">+ Rp 278.570</span>
                        </div>

                        <!-- Tunjangan Anak -->
                        <div class="flex justify-between items-center text-sm">
                            <div>
                                <span class="text-slate-200 block">Tunjangan Anak</span>
                                <span id="res-anak-label" class="text-[11px] text-emerald-400">1 Anak (2% × Gaji Pokok)</span>
                            </div>
                            <span id="res-tunj-anak" class="font-semibold text-emerald-300">+ Rp 55.714</span>
                        </div>

                        <!-- Kotak Highlight Total Tunjangan Keluarga -->
                        <div class="bg-emerald-950/60 border border-emerald-500/40 rounded-xl p-4 mt-2">
                            <div class="flex justify-between items-center">
                                <span class="text-xs font-semibold uppercase tracking-wide text-emerald-300">Total Tunjangan Keluarga</span>
                                <span id="res-total-persen-text" class="text-xs font-bold text-emerald-400">(12%)</span>
                            </div>
                            <div id="res-total-tunjangan" class="font-display text-2xl sm:text-3xl font-extrabold text-emerald-400 mt-1">
                                Rp 334.284
                            </div>
                        </div>

                        <!-- Kotak Total Gaji Pokok + Tunjangan Keluarga -->
                        <div class="bg-navy-950/80 border border-white/10 rounded-xl p-4">
                            <span class="text-xs text-slate-400 block">Total Gaji Pokok + Tunjangan Keluarga</span>
                            <div id="res-grand-total" class="font-display text-xl sm:text-2xl font-bold text-white mt-0.5">
                                Rp 3.119.984
                            </div>
                            <p class="text-[10px] text-slate-400 mt-1">*Belum termasuk tunjangan jabatan/umum, tunjangan beras, dan potongan wajib (IWP/PPh).</p>
                        </div>

                        <!-- Tombol Simpan ke Riwayat -->
                        <button type="button" onclick="simpanKeRiwayat()" class="w-full py-3 px-4 rounded-xl bg-emerald-600 hover:bg-emerald-500 text-white font-semibold text-sm shadow-lg shadow-emerald-950/50 flex items-center justify-center gap-2 transition cursor-pointer">
                            <i data-lucide="bookmark-plus" class="w-4 h-4"></i>
                            <span>Simpan ke Riwayat Simulasi</span>
                        </button>
                    </div>
                </div>
            </div>
        </div>

        <!-- Bagian Riwayat Pengecekan / Simulasi -->
        <section class="bg-white rounded-2xl shadow-sm border border-slate-200/80 overflow-hidden">
            <div class="px-6 py-5 border-b border-slate-100 flex flex-col sm:flex-row justify-between items-start sm:items-center gap-3">
                <div class="flex items-center gap-3">
                    <div class="w-9 h-9 rounded-xl bg-emerald-50 text-emerald-700 flex items-center justify-center border border-emerald-200">
                        <i data-lucide="history" class="w-5 h-5"></i>
                    </div>
                    <div>
                        <h3 class="font-display font-bold text-base sm:text-lg text-navy-900">Riwayat Pengecekan & Simulasi</h3>
                        <p class="text-xs text-slate-500">Bandingkan hasil simulasi perhitungan tunjangan sebelum dan sesudah perubahan status keluarga atau golongan.</p>
                    </div>
                </div>
                <button id="btn-hapus-semua" onclick="hapusSemuaRiwayat()" class="hidden inline-flex items-center gap-1.5 px-3.5 py-2 rounded-xl border border-rose-200 bg-rose-50 hover:bg-rose-100 text-rose-700 text-xs font-semibold transition cursor-pointer">
                    <i data-lucide="trash-2" class="w-3.5 h-3.5"></i>
                    <span>Hapus Semua Riwayat</span>
                </button>
            </div>

            <div class="overflow-x-auto">
                <table class="w-full text-left border-collapse">
                    <thead>
                        <tr class="bg-slate-50 text-slate-500 text-[11px] uppercase tracking-wider border-b border-slate-200">
                            <th class="py-3.5 px-4 font-semibold">Waktu & Identitas</th>
                            <th class="py-3.5 px-4 font-semibold">Golongan & Gaji Pokok</th>
                            <th class="py-3.5 px-4 font-semibold">Susunan Keluarga</th>
                            <th class="py-3.5 px-4 font-semibold">Rincian Tunjangan</th>
                            <th class="py-3.5 px-4 font-semibold">Total Tunj. Keluarga</th>
                            <th class="py-3.5 px-4 font-semibold">Total Gapok + Tunj.</th>
                            <th class="py-3.5 px-4 font-semibold text-right">Aksi</th>
                        </tr>
                    </thead>
                    <tbody id="tbody-riwayat" class="divide-y divide-slate-100 text-sm">
                        <!-- Rendered via JS -->
                    </tbody>
                </table>
            </div>
        </section>

        <!-- Panel Edukasi & Informasi Regulasi Ringkas -->
        <section id="panel-regulasi" class="bg-white rounded-2xl shadow-sm border border-slate-200/80 p-6">
            <div class="flex items-center gap-2.5 mb-4">
                <div class="w-8 h-8 rounded-lg bg-navy-900 text-gold-400 flex items-center justify-center">
                    <i data-lucide="scale" class="w-4 h-4"></i>
                </div>
                <div>
                    <h3 class="font-display font-bold text-base text-navy-900">Dasar Hukum & Ketentuan Tunjangan Keluarga ASN</h3>
                    <p class="text-xs text-slate-500">Mengacu pada PP Nomor 7 Tahun 1977 jo. PP Nomor 5 Tahun 2024 tentang Peraturan Gaji PNS</p>
                </div>
            </div>

            <div class="grid grid-cols-1 md:grid-cols-3 gap-4 text-xs">
                <div class="p-4 rounded-xl bg-slate-50 border border-slate-200/80 space-y-1.5">
                    <span class="inline-block font-bold text-navy-900 bg-navy-900/10 px-2.5 py-0.5 rounded-md">1. Tunjangan Istri / Suami (10%)</span>
                    <p class="text-slate-600 leading-relaxed pt-1">
                        Diberikan sebesar <strong>10% dari Gaji Pokok</strong>. Apabila suami dan istri keduanya berkedudukan sebagai ASN (PNS/PPPK/TNI/Polri), maka tunjangan keluarga hanya diberikan kepada salah satu yang mempunyai <strong>Gaji Pokok lebih tinggi</strong>.
                    </p>
                </div>

                <div class="p-4 rounded-xl bg-slate-50 border border-slate-200/80 space-y-1.5">
                    <span class="inline-block font-bold text-emerald-800 bg-emerald-100 px-2.5 py-0.5 rounded-md">2. Tunjangan Anak (2% / Anak)</span>
                    <p class="text-slate-600 leading-relaxed pt-1">
                        Diberikan sebesar <strong>2% dari Gaji Pokok</strong> untuk setiap anak (anak kandung, anak tiri, atau anak angkat yang sah) dengan jumlah maksimal <strong>2 (dua) orang anak</strong> yang masuk dalam daftar gaji.
                    </p>
                </div>

                <div class="p-4 rounded-xl bg-slate-50 border border-slate-200/80 space-y-1.5">
                    <span class="inline-block font-bold text-amber-800 bg-amber-100 px-2.5 py-0.5 rounded-md">3. Syarat & Penghentian</span>
                    <p class="text-slate-600 leading-relaxed pt-1">
                        Tunjangan anak dihentikan apabila anak telah mencapai usia <strong>21 tahun</strong> (kecuali masih sekolah/kuliah maksimal <strong>25 tahun</strong>), telah menikah, atau telah mempunyai penghasilan sendiri.
                    </p>
                </div>
            </div>
        </section>

    </main>

    <!-- Footer Resmi -->
    <footer class="bg-navy-950 text-slate-400 py-8 border-t border-slate-800 mt-10">
        <div class="max-w-6xl mx-auto px-4 sm:px-6 lg:px-8 space-y-6">
            <!-- Kartu Statistik Pengunjung Real-Time -->
            <div class="bg-navy-900/90 border border-slate-800 rounded-2xl p-4 sm:p-5 flex flex-col sm:flex-row items-center justify-between gap-4 shadow-inner">
                <div class="flex items-center gap-3.5 text-center sm:text-left">
                    <div class="w-11 h-11 rounded-xl bg-emerald-500/15 border border-emerald-500/30 text-emerald-400 flex items-center justify-center shrink-0">
                        <i data-lucide="bar-chart-3" class="w-5 h-5"></i>
                    </div>
                    <div>
                        <div class="flex flex-wrap items-center justify-center sm:justify-start gap-2">
                            <h4 class="font-display font-bold text-sm text-white">Statistik Kunjungan Layanan</h4>
                            <span id="visitor-status-badge" class="inline-flex items-center gap-1.5 text-[10px] font-semibold px-2 py-0.5 rounded-full bg-emerald-500/15 text-emerald-300 border border-emerald-500/30">
                                <span class="w-1.5 h-1.5 rounded-full bg-emerald-400 animate-pulse"></span>
                                <span>Live Counter</span>
                            </span>
                        </div>
                        <p class="text-xs text-slate-400 mt-0.5">Total akses halaman SI TUKEL oleh pegawai dari seluruh perangkat</p>
                    </div>
                </div>

                <!-- Angka Penghitung Pengunjung -->
                <div class="flex items-center gap-3 bg-navy-950/90 border border-slate-800 px-5 py-3 rounded-xl shrink-0">
                    <div class="text-right">
                        <span class="block text-[10px] uppercase tracking-wider font-semibold text-slate-400">Total Kunjungan</span>
                        <div class="flex items-baseline justify-end gap-1.5 mt-0.5">
                            <span id="visitor-count-display" class="font-display font-extrabold text-2xl sm:text-3xl text-gold-400 tracking-tight">...</span>
                            <span class="text-xs font-medium text-slate-400">kali diakses</span>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Baris Hak Cipta & Regulasi -->
            <div class="flex flex-col sm:flex-row justify-between items-center gap-3 text-xs text-center sm:text-left pt-2 border-t border-slate-800/80">
                <div>
                    <p class="font-semibold text-white">SI TUKEL — Pemerintah Kabupaten Keerom</p>
                    <p class="text-[11px] text-slate-400 mt-0.5">Layanan Informasi & Simulasi Mandiri Tunjangan Keluarga Aparatur Sipil Negara</p>
                </div>
                <div class="text-[11px] text-slate-500">
                    Referensi Perhitungan: PP No. 7 Tahun 1977 jo. PP No. 5 Tahun 2024
                </div>
            </div>
        </div>
    </footer>

    <!-- ==========================================
         JAVASCRIPT LOGIC
         ========================================== -->
    <script>
        const STORAGE_KEY = 'situkel_keerom_history_v1';
        const VISITOR_FALLBACK_KEY = 'situkel_keerom_visitor_fallback_v1';
        const COUNTER_API_URL = 'https://api.counterapi.dev/v1/situkel-keerom/visits/up';
        let simulationHistory = [];
        let currentCalcResult = null;

        document.addEventListener('DOMContentLoaded', () => {
            loadHistory();
            hitungTunjangan();
            renderHistoryTable();
            initVisitorCounter();
            lucide.createIcons();
        });

        // Inisialisasi & Pembaruan Real-Time Visitor Counter
        async function initVisitorCounter() {
            const countEl = document.getElementById('visitor-count-display');
            const badgeEl = document.getElementById('visitor-status-badge');

            try {
                const response = await fetch(COUNTER_API_URL, {
                    method: 'GET',
                    cache: 'no-store'
                });

                if (!response.ok) {
                    throw new Error('Gagal terhubung ke server counter');
                }

                const data = await response.json();
                const totalVisits = Number(data.count) || 1;

                // Sinkronkan nilai terbaru ke penyimpanan lokal sebagai cadangan
                localStorage.setItem(VISITOR_FALLBACK_KEY, String(totalVisits));
                countEl.textContent = totalVisits.toLocaleString('id-ID');
            } catch (error) {
                // Fallback otomatis ke localStorage apabila perangkat sedang offline
                const savedLocal = parseInt(localStorage.getItem(VISITOR_FALLBACK_KEY) || '0', 10);
                const updatedLocal = savedLocal + 1;
                localStorage.setItem(VISITOR_FALLBACK_KEY, String(updatedLocal));

                countEl.textContent = updatedLocal.toLocaleString('id-ID');
                if (badgeEl) {
                    badgeEl.className = 'inline-flex items-center gap-1.5 text-[10px] font-semibold px-2 py-0.5 rounded-full bg-amber-500/15 text-amber-300 border border-amber-500/30';
                    badgeEl.innerHTML = '<span class="w-1.5 h-1.5 rounded-full bg-amber-400"></span><span>Mode Lokal</span>';
                }
            }
        }

        // Format angka menjadi Rupiah (Rp 2.785.700)
        function formatRupiah(angka) {
            return 'Rp ' + Math.round(angka).toLocaleString('id-ID');
        }

        // Ambil angka murni dari string input berformat titik
        function parseAngka(str) {
            return parseInt(String(str).replace(/\D/g, ''), 10) || 0;
        }

        // Ketika user memilih Golongan dari dropdown
        function handleGolonganChange() {
            const val = document.getElementById('inp-golongan').value;
            if (val !== 'custom') {
                const nominal = parseInt(val.split('|')[0], 10);
                document.getElementById('inp-gapok').value = nominal.toLocaleString('id-ID');
            }
            hitungTunjangan();
        }

        // Ketika user mengetik manual nominal Gaji Pokok
        function handleManualGapok(el) {
            let raw = el.value.replace(/\D/g, '');
            el.value = raw ? parseInt(raw, 10).toLocaleString('id-ID') : '';
            document.getElementById('inp-golongan').value = 'custom';
            hitungTunjangan();
        }

        // Kalkulasi Real-Time Tunjangan Keluarga
        function hitungTunjangan() {
            const gapok = parseAngka(document.getElementById('inp-gapok').value);
            const persenNikah = parseFloat(document.querySelector('input[name="status_nikah"]:checked').value) || 0;
            const jumlahAnak = parseInt(document.querySelector('input[name="jumlah_anak"]:checked').value, 10) || 0;
            const persenAnak = jumlahAnak * 0.02;

            const tunjNikah = Math.round(gapok * persenNikah);
            const tunjAnak = Math.round(gapok * persenAnak);
            const totalTunjangan = tunjNikah + tunjAnak;
            const grandTotal = gapok + totalTunjangan;
            const totalPersen = Math.round((persenNikah + persenAnak) * 100);

            // Update Tampilan Kartu Rincian
            document.getElementById('res-gapok').textContent = formatRupiah(gapok);
            document.getElementById('res-tunj-nikah').textContent = persenNikah > 0 ? '+ ' + formatRupiah(tunjNikah) : 'Rp 0';
            document.getElementById('res-nikah-label').textContent = persenNikah > 0 ? '10% × Gaji Pokok (Menikah)' : '0% (Belum Menikah)';

            document.getElementById('res-tunj-anak').textContent = jumlahAnak > 0 ? '+ ' + formatRupiah(tunjAnak) : 'Rp 0';
            document.getElementById('res-anak-label').textContent = jumlahAnak > 0
                ? `${jumlahAnak} Anak (${jumlahAnak * 2}% × Gaji Pokok)`
                : '0 Anak (0%)';

            document.getElementById('res-total-tunjangan').textContent = formatRupiah(totalTunjangan);
            document.getElementById('res-total-persen-text').textContent = `(${totalPersen}%)`;
            document.getElementById('badge-total-persen').textContent = `Tunjangan +${totalPersen}%`;
            document.getElementById('res-grand-total').textContent = formatRupiah(grandTotal);

            // Simpan state hasil terkini
            const golSelect = document.getElementById('inp-golongan');
            const golLabel = golSelect.value === 'custom'
                ? 'Input Manual'
                : golSelect.value.split('|')[1];

            currentCalcResult = {
                gapok,
                golonganLabel: golLabel,
                isMenikah: persenNikah > 0,
                jumlahAnak,
                tunjNikah,
                tunjAnak,
                totalTunjangan,
                grandTotal,
                totalPersen
            };
        }

        // Reset Parameter ke Default
        function resetKalkulator() {
            document.getElementById('inp-nama').value = '';
            document.getElementById('inp-nip').value = '';
            document.getElementById('inp-golongan').value = '2785700|Golongan III.a (MKG 0 Thn)';
            document.getElementById('inp-gapok').value = '2.785.700';
            document.querySelector('input[name="status_nikah"][value="0.10"]').checked = true;
            document.querySelector('input[name="jumlah_anak"][value="1"]').checked = true;
            hitungTunjangan();
            showToast('Parameter perhitungan dikembalikan ke pengaturan awal.', 'info');
        }

        // Simpan Hasil Simulasi ke LocalStorage
        function simpanKeRiwayat() {
            if (!currentCalcResult || currentCalcResult.gapok <= 0) {
                showToast('Masukkan nominal Gaji Pokok yang valid terlebih dahulu.', 'error');
                return;
            }

            const namaInput = document.getElementById('inp-nama').value.trim();
            const nipInput = document.getElementById('inp-nip').value.trim();

            const now = new Date();
            const waktuStr = now.toLocaleDateString('id-ID', {
                day: '2-digit', month: 'short', year: 'numeric'
            }) + ' • ' + now.toLocaleTimeString('id-ID', { hour: '2-digit', minute: '2-digit' });

            const entry = {
                id: 'SIM-' + Date.now(),
                waktu: waktuStr,
                nama: namaInput || 'Simulasi Mandiri ASN',
                nip: nipInput || '-',
                ...currentCalcResult
            };

            simulationHistory.unshift(entry);
            saveHistory();
            renderHistoryTable();
            showToast('Hasil perhitungan berhasil disimpan ke Riwayat Simulasi.', 'success');
        }

        function loadHistory() {
            try {
                const raw = localStorage.getItem(STORAGE_KEY);
                simulationHistory = raw ? JSON.parse(raw) : [];
            } catch (e) {
                simulationHistory = [];
            }
        }

        function saveHistory() {
            localStorage.setItem(STORAGE_KEY, JSON.stringify(simulationHistory));
        }

        function hapusItemRiwayat(id) {
            simulationHistory = simulationHistory.filter(item => item.id !== id);
            saveHistory();
            renderHistoryTable();
            showToast('Item riwayat dihapus.', 'info');
        }

        function hapusSemuaRiwayat() {
            simulationHistory = [];
            saveHistory();
            renderHistoryTable();
            showToast('Seluruh riwayat simulasi telah dibersihkan.', 'info');
        }

        // Render Tabel Riwayat Simulasi
        function renderHistoryTable() {
            const tbody = document.getElementById('tbody-riwayat');
            const btnHapusSemua = document.getElementById('btn-hapus-semua');

            if (simulationHistory.length === 0) {
                btnHapusSemua.classList.add('hidden');
                tbody.innerHTML = `
                    <tr>
                        <td colspan="7" class="py-10 px-4 text-center">
                            <div class="w-11 h-11 rounded-full bg-slate-100 text-slate-400 flex items-center justify-center mx-auto mb-2">
                                <i data-lucide="calculator" class="w-5 h-5"></i>
                            </div>
                            <p class="text-sm font-medium text-slate-600">Belum ada riwayat simulasi yang disimpan</p>
                            <p class="text-xs text-slate-400 mt-0.5">Klik tombol <strong>"Simpan ke Riwayat Simulasi"</strong> pada kartu rincian untuk menyimpan perbandingan perhitungan Anda.</p>
                        </td>
                    </tr>
                `;
                lucide.createIcons();
                return;
            }

            btnHapusSemua.classList.remove('hidden');
            tbody.innerHTML = simulationHistory.map(item => `
                <tr class="hover:bg-slate-50/90 transition">
                    <td class="py-3.5 px-4 align-top">
                        <div class="font-semibold text-slate-800 text-xs sm:text-sm">${escapeHTML(item.nama)}</div>
                        ${item.nip !== '-' ? `<div class="text-[11px] font-mono text-slate-500">NIP. ${escapeHTML(item.nip)}</div>` : ''}
                        <div class="text-[11px] text-slate-400 mt-0.5">${item.waktu}</div>
                    </td>
                    <td class="py-3.5 px-4 align-top">
                        <div class="font-bold text-navy-900 text-xs sm:text-sm">${formatRupiah(item.gapok)}</div>
                        <div class="text-[11px] text-slate-500">${escapeHTML(item.golonganLabel)}</div>
                    </td>
                    <td class="py-3.5 px-4 align-top">
                        <span class="inline-flex items-center px-2 py-0.5 rounded-md text-[11px] font-semibold ${item.isMenikah ? 'bg-emerald-50 text-emerald-700 border border-emerald-200' : 'bg-slate-100 text-slate-600'}">
                            ${item.isMenikah ? 'Menikah (10%)' : 'Belum Menikah (0%)'}
                        </span>
                        <div class="text-xs text-slate-600 mt-1">${item.jumlahAnak} Anak Tertanggung (${item.jumlahAnak * 2}%)</div>
                    </td>
                    <td class="py-3.5 px-4 align-top text-xs space-y-0.5">
                        <div class="text-slate-600">Pasangan: <strong class="text-slate-800">${formatRupiah(item.tunjNikah)}</strong></div>
                        <div class="text-slate-600">Anak: <strong class="text-slate-800">${formatRupiah(item.tunjAnak)}</strong></div>
                    </td>
                    <td class="py-3.5 px-4 align-top">
                        <span class="font-display font-bold text-emerald-700 text-sm">${formatRupiah(item.totalTunjangan)}</span>
                        <span class="block text-[11px] text-emerald-600 font-medium">+${item.totalPersen}% dari Gapok</span>
                    </td>
                    <td class="py-3.5 px-4 align-top">
                        <span class="font-display font-bold text-navy-900 text-sm">${formatRupiah(item.grandTotal)}</span>
                    </td>
                    <td class="py-3.5 px-4 align-top text-right">
                        <button onclick="hapusItemRiwayat('${item.id}')" title="Hapus item ini" class="p-2 rounded-lg text-slate-400 hover:text-rose-600 hover:bg-rose-50 transition cursor-pointer">
                            <i data-lucide="trash-2" class="w-4 h-4"></i>
                        </button>
                    </td>
                </tr>
            `).join('');

            lucide.createIcons();
        }

        function scrollToRegulasi() {
            document.getElementById('panel-regulasi').scrollIntoView({ behavior: 'smooth' });
        }

        // Toggle Buka/Tutup Panel Persyaratan Pengajuan Tunjangan Keluarga
        function togglePersyaratan(forceState) {
            const body = document.getElementById('persyaratan-accordion-body');
            const btn = document.getElementById('btn-toggle-persyaratan');
            const icon = document.getElementById('icon-chevron-persyaratan');
            const badge = document.getElementById('badge-status-persyaratan');
            const label = document.getElementById('label-toggle-persyaratan');
            const panel = document.getElementById('panel-persyaratan');

            if (!body || !btn) return;

            const isCurrentlyOpen = body.classList.contains('is-open');
            const shouldOpen = typeof forceState === 'boolean' ? forceState : !isCurrentlyOpen;

            if (shouldOpen) {
                body.classList.add('is-open');
                btn.setAttribute('aria-expanded', 'true');
                if (icon) icon.style.transform = 'rotate(180deg)';
                if (badge) {
                    badge.textContent = 'Tutup Persyaratan';
                    badge.className = 'inline-flex items-center gap-1 text-[11px] font-bold px-2.5 py-0.5 rounded-full bg-amber-500/20 text-amber-300 border border-amber-400/30 transition-colors';
                }
                if (label) label.textContent = 'Tutup Persyaratan';
                if (forceState === true && panel) {
                    panel.scrollIntoView({ behavior: 'smooth', block: 'nearest' });
                }
            } else {
                body.classList.remove('is-open');
                btn.setAttribute('aria-expanded', 'false');
                if (icon) icon.style.transform = 'rotate(0deg)';
                if (badge) {
                    badge.textContent = 'Klik untuk Lihat Persyaratan';
                    badge.className = 'inline-flex items-center gap-1 text-[11px] font-bold px-2.5 py-0.5 rounded-full bg-emerald-500/20 text-emerald-300 border border-emerald-400/30 transition-colors';
                }
                if (label) label.textContent = 'Klik untuk Lihat Persyaratan';
            }
        }

        function escapeHTML(str) {
            if (!str) return '';
            return String(str)
                .replace(/&/g, '&amp;')
                .replace(/</g, '&lt;')
                .replace(/>/g, '&gt;')
                .replace(/"/g, '&quot;');
        }

        function showToast(message, type = 'success') {
            const container = document.getElementById('toast-container');
            const toast = document.createElement('div');

            const styles = {
                success: 'bg-emerald-900 text-white border-emerald-700',
                error: 'bg-rose-900 text-white border-rose-700',
                info: 'bg-navy-900 text-white border-navy-700'
            };

            const icons = {
                success: 'check-circle-2',
                error: 'alert-circle',
                info: 'info'
            };

            toast.className = `pointer-events-auto flex items-center gap-3 px-4 py-3 rounded-xl shadow-lg border text-xs sm:text-sm font-medium transition-all transform translate-y-2 opacity-0 ${styles[type] || styles.info}`;
            toast.innerHTML = `
                <i data-lucide="${icons[type] || 'info'}" class="w-5 h-5 shrink-0 text-gold-400"></i>
                <span class="flex-1">${escapeHTML(message)}</span>
            `;

            container.appendChild(toast);
            lucide.createIcons();

            requestAnimationFrame(() => {
                toast.classList.remove('translate-y-2', 'opacity-0');
            });

            setTimeout(() => {
                toast.classList.add('opacity-0', 'translate-y-2');
                setTimeout(() => toast.remove(), 300);
            }, 3500);
        }
    </script>
</body>
</html>
```
