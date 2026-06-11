<!-- AIGenius - Redesigned Dashboard -->
<!DOCTYPE html><html class="light" lang="id" style=""><head>
<meta charset="utf-8">
<meta content="width=device-width, initial-scale=1.0" name="viewport">
<title>AIGenius Web Builder - Dashboard</title>
<script src="https://cdn.tailwindcss.com?plugins=forms,container-queries"></script>
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700&amp;family=JetBrains+Mono:wght@400&amp;family=Material+Symbols+Outlined:wght,FILL@100..700,0..1&amp;display=swap" rel="stylesheet">
<style>
        .material-symbols-outlined {
            font-variation-settings: 'FILL' 0, 'wght' 400, 'GRAD' 0, 'opsz' 24;
        }
        .glass-effect {
            background: rgba(255, 255, 255, 0.7);
            backdrop-filter: blur(12px);
            -webkit-backdrop-filter: blur(12px);
        }
        .custom-scrollbar::-webkit-scrollbar {
            width: 8px;
        }
        .custom-scrollbar::-webkit-scrollbar-track {
            background: transparent;
        }
        .custom-scrollbar::-webkit-scrollbar-thumb {
            background: #cbd5e1;
            border-radius: 4px;
        }
        .skeleton-card.selected {
            border-color: #3525cd;
            background-color: #f0efff;
            box-shadow: 0 0 0 2px #3525cd;
        }
    </style>
<script id="tailwind-config">
        tailwind.config = {
          darkMode: "class",
          theme: {
            extend: {
              "colors": {
                      "surface-container-highest": "#d3e4fe",
                      "on-secondary-container": "#004666",
                      "surface-dim": "#cbdbf5",
                      "outline-variant": "#c7c4d8",
                      "on-surface-variant": "#464555",
                      "primary-fixed": "#e2dfff",
                      "on-primary-fixed": "#0f0069",
                      "background": "#f8f9ff",
                      "surface-container-lowest": "#ffffff",
                      "on-secondary": "#ffffff",
                      "surface-container-high": "#dce9ff",
                      "on-primary-container": "#dad7ff",
                      "outline": "#777587",
                      "on-background": "#0b1c30",
                      "secondary-fixed-dim": "#89ceff",
                      "error-container": "#ffdad6",
                      "on-tertiary-container": "#ffd0d2",
                      "inverse-surface": "#213145",
                      "primary-fixed-dim": "#c3c0ff",
                      "on-tertiary-fixed-variant": "#92002a",
                      "secondary-fixed": "#c9e6ff",
                      "surface-bright": "#f8f9ff",
                      "inverse-primary": "#c3c0ff",
                      "on-tertiary": "#ffffff",
                      "tertiary-fixed": "#ffdadb",
                      "primary": "#3525cd",
                      "surface-container-low": "#eff4ff",
                      "tertiary-container": "#bf0f3c",
                      "inverse-on-surface": "#eaf1ff",
                      "surface-tint": "#4d44e3",
                      "on-primary": "#ffffff",
                      "secondary-container": "#39b8fd",
                      "on-secondary-fixed": "#001e2f",
                      "tertiary": "#95002b",
                      "on-tertiary-fixed": "#40000d",
                      "error": "#ba1a1a",
                      "secondary": "#006591",
                      "on-surface": "#0b1c30",
                      "surface": "#f8f9ff",
                      "primary-container": "#4f46e5",
                      "tertiary-fixed-dim": "#ffb2b7",
                      "on-primary-fixed-variant": "#3323cc",
                      "on-error-container": "#93000a",
                      "on-error": "#ffffff",
                      "surface-container": "#e5eeff"
              },
              "borderRadius": {
                      "DEFAULT": "0.25rem",
                      "lg": "0.5rem",
                      "xl": "0.75rem",
                      "full": "9999px"
              },
              "spacing": {
                      "margin-desktop": "48px",
                      "container-max": "1280px",
                      "margin-mobile": "16px",
                      "gutter": "24px",
                      "base": "8px"
              },
              "fontFamily": {
                      "headline-md": ["Inter"],
                      "code-sm": ["JetBrains Mono"],
                      "body-lg": ["Inter"],
                      "display-lg": ["Inter"],
                      "label-caps": ["Inter"],
                      "display-lg-mobile": ["Inter"],
                      "body-md": ["Inter"]
              },
              "fontSize": {
                      "headline-md": ["24px", {"lineHeight": "32px", "fontWeight": "600"}],
                      "code-sm": ["14px", {"lineHeight": "20px", "fontWeight": "400"}],
                      "body-lg": ["18px", {"lineHeight": "28px", "fontWeight": "400"}],
                      "display-lg": ["48px", {"lineHeight": "56px", "letterSpacing": "-0.02em", "fontWeight": "700"}],
                      "label-caps": ["12px", {"lineHeight": "16px", "letterSpacing": "0.05em", "fontWeight": "600"}],
                      "display-lg-mobile": ["32px", {"lineHeight": "40px", "letterSpacing": "-0.01em", "fontWeight": "700"}],
                      "body-md": ["16px", {"lineHeight": "24px", "fontWeight": "400"}]
              }
            },
          },
        }
      </script>
</head>
<body class="bg-background text-on-surface font-body-md min-h-screen flex flex-col">
<!-- Top Navigation Bar -->
<header class="w-full top-0 sticky z-50 bg-surface-container-lowest dark:bg-surface-dim shadow-sm">
<div class="flex justify-between items-center h-16 px-margin-desktop max-w-container-max mx-auto">
<div class="flex items-center gap-base">
<span class="material-symbols-outlined text-primary text-3xl" style="font-variation-settings: &quot;FILL&quot; 1;">auto_awesome</span>
<span class="text-headline-md font-headline-md font-bold text-primary dark:text-primary-fixed">AIGenius</span>
</div>
<nav class="hidden md:flex items-center gap-gutter">
<a class="font-label-caps text-label-caps text-primary dark:text-primary-fixed-dim border-b-2 border-primary dark:border-primary-fixed-dim pb-1" href="#">Dashboard</a>
<a class="font-label-caps text-label-caps text-on-surface-variant dark:text-outline-variant hover:text-primary transition-colors" href="#">Projects</a>

<a class="font-label-caps text-label-caps text-on-surface-variant dark:text-outline-variant hover:text-primary transition-colors" href="#">Billing</a>
</nav>
<div class="flex items-center gap-4">
<button class="font-label-caps text-label-caps text-on-surface-variant hover:bg-surface-container-low px-4 py-2 rounded-lg transition-all">Help</button>
<button class="bg-primary text-on-primary px-6 py-2 rounded-lg font-label-caps text-label-caps active:scale-95 transition-transform shadow-sm hover:opacity-90">Deploy</button>
<div class="w-10 h-10 rounded-full bg-surface-container-high overflow-hidden border border-outline-variant">
<img alt="User Profile Avatar" class="w-full h-full object-cover" src="https://lh3.googleusercontent.com/aida-public/AB6AXuAlBw1wNPjZzHI0bpwWnSpHKNzPB96g7vUJLoFiMGUdkZsCqwyR2b_EAuVfb3ntgVw76H1VEJqAc-x6S6FKnERplCnaak3GyBjiiq4PkVPyyr9mzKUba8oyz1QmeEkAQhOw0tr4ML7T_2oa4E4VjQNyAmfgqUL9eyna2izKr7WjofBxLBxpkk7tTUuw3W2hGl6yzoNt1iqymocrPJ6veRxikCcvf-gGkr92mkFKfKF9iWyreEaNl8jM2ApajInu4JyWv0HLOqI7xCg">
</div>
</div>
</div>
</header>
<main class="flex-grow max-w-4xl mx-auto w-full px-margin-mobile md:px-0 py-12 flex flex-col gap-16">
<!-- 1. AI Chatbox Section (Centered Flow) -->
<section class="bg-surface-container-lowest rounded-2xl border border-outline-variant overflow-hidden flex flex-col h-[500px] shadow-sm">
<div class="px-6 py-4 border-b border-outline-variant flex items-center justify-between bg-surface-container-low">
<div class="flex items-center gap-3">
<span class="material-symbols-outlined text-primary" style="font-variation-settings: &quot;FILL&quot; 1;">smart_toy</span>
<h2 class="font-headline-md text-headline-md text-on-surface">AI Generator Assistant</h2>
</div>
<div class="flex items-center gap-2">
<span class="w-2 h-2 rounded-full bg-emerald-500 animate-pulse"></span>

</div>
</div>
<div class="flex-grow p-6 overflow-y-auto flex flex-col gap-6 custom-scrollbar">
<!-- AI Message -->
<div class="flex gap-3 max-w-[85%]">
<div class="w-9 h-9 rounded-full bg-primary flex items-center justify-center flex-shrink-0 shadow-sm">
<span class="material-symbols-outlined text-white text-lg">bolt</span>
</div>
<div class="bg-surface-container text-on-surface p-4 rounded-2xl rounded-tl-none border border-outline-variant/30">
<p class="font-body-md text-body-md">Halo! Saya siap membantu Anda membangun website hari ini. Apa yang ingin Anda buat?</p>
</div>
</div>
<!-- User Message -->
<div class="flex gap-3 max-w-[85%] self-end flex-row-reverse">
<div class="w-9 h-9 rounded-full bg-secondary flex items-center justify-center flex-shrink-0 shadow-sm">
<span class="material-symbols-outlined text-white text-lg">person</span>
</div>
<div class="bg-primary-container text-on-primary p-4 rounded-2xl rounded-tr-none shadow-sm">
<p class="font-body-md text-body-md">Buatkan saya landing page modern untuk agensi desain dengan nuansa minimalis.</p>
</div>
</div>
<!-- AI Response -->
<div class="flex gap-3 max-w-[85%]">
<div class="w-9 h-9 rounded-full bg-primary flex items-center justify-center flex-shrink-0 shadow-sm">
<span class="material-symbols-outlined text-white text-lg">bolt</span>
</div>
<div class="bg-surface-container text-on-surface p-4 rounded-2xl rounded-tl-none border border-outline-variant/30">
<p class="font-body-md text-body-md">Tentu! Saya sedang memproses struktur landing page untuk agensi desain. Berikut adalah draf awalnya. Anda bisa memilih paket dan template di bawah ini untuk melanjutkan.</p>
</div>
</div>
</div>
<div class="p-6 bg-surface-container-low border-t border-outline-variant">
<div class="relative flex items-center">
<input class="w-full bg-surface-container-lowest border border-outline-variant rounded-full py-4 pl-6 pr-14 focus:ring-2 focus:ring-primary focus:border-transparent outline-none transition-all shadow-sm" placeholder="Ketik instruksi pembuatan website..." type="text">
<button class="absolute right-2 p-2 bg-primary text-white rounded-full hover:opacity-90 transition-opacity shadow-md">
<span class="material-symbols-outlined">send</span>
</button>
</div>
</div>
</section>
<!-- 2. Product List Table Section -->
<section class="flex flex-col gap-6">
<div class="flex items-center justify-between">
<h3 class="font-headline-md text-display-lg-mobile text-on-surface">Product List</h3>
<span class="text-on-surface-variant text-sm font-label-caps">Langkah 2 dari 3</span>
</div>
<div class="bg-surface-container-lowest rounded-2xl border border-outline-variant overflow-hidden shadow-sm">
<table class="w-full text-left border-collapse">
<thead>
<tr class="bg-surface-container-low border-b border-outline-variant">
<th class="px-8 py-5 font-label-caps text-label-caps text-on-surface">Nama Produk</th>
<th class="px-8 py-5 font-label-caps text-label-caps text-on-surface">Fitur Unggulan</th>
<th class="px-8 py-5 font-label-caps text-label-caps text-on-surface text-right">Harga Satuan</th>
</tr>
</thead>
<tbody class="divide-y divide-outline-variant/50">
<tr class="group hover:bg-surface-container-low/50 transition-colors cursor-pointer"><td class="px-8 py-6"><div class="flex items-center gap-3"><div class="w-5 h-5 rounded-full bg-outline-variant/30 animate-pulse"></div><div class="h-5 w-24 bg-outline-variant/30 rounded animate-pulse"></div></div></td><td class="px-8 py-6"><div class="flex flex-wrap gap-2"><div class="h-4 w-12 bg-outline-variant/30 rounded animate-pulse"></div><div class="h-4 w-16 bg-outline-variant/30 rounded animate-pulse"></div></div></td><td class="px-8 py-6 text-right"><div class="h-6 w-20 bg-outline-variant/30 rounded animate-pulse ml-auto"></div></td></tr>
<tr class="group hover:bg-surface-container-low/50 transition-colors cursor-pointer"><td class="px-8 py-6"><div class="flex items-center gap-3"><div class="w-5 h-5 rounded-full bg-outline-variant/30 animate-pulse"></div><div class="h-5 w-32 bg-outline-variant/30 rounded animate-pulse"></div></div></td><td class="px-8 py-6"><div class="flex flex-wrap gap-2"><div class="h-4 w-16 bg-outline-variant/30 rounded animate-pulse"></div><div class="h-4 w-16 bg-outline-variant/30 rounded animate-pulse"></div><div class="h-4 w-20 bg-outline-variant/30 rounded animate-pulse"></div></div></td><td class="px-8 py-6 text-right"><div class="h-6 w-24 bg-outline-variant/30 rounded animate-pulse ml-auto"></div></td></tr>
<tr class="group hover:bg-surface-container-low/50 transition-colors cursor-pointer"><td class="px-8 py-6"><div class="flex items-center gap-3"><div class="w-5 h-5 rounded-full bg-outline-variant/30 animate-pulse"></div><div class="h-5 w-28 bg-outline-variant/30 rounded animate-pulse"></div></div></td><td class="px-8 py-6"><div class="flex flex-wrap gap-2"><div class="h-4 w-32 bg-outline-variant/30 rounded animate-pulse"></div><div class="h-4 w-24 bg-outline-variant/30 rounded animate-pulse"></div></div></td><td class="px-8 py-6 text-right"><div class="h-6 w-16 bg-outline-variant/30 rounded animate-pulse ml-auto"></div></td></tr>
</tbody>
</table>
</div>
<!-- 3. Approve Action Button -->
<div class="flex justify-center pt-4">
<button class="bg-primary text-on-primary px-12 py-4 rounded-xl font-headline-md text-lg hover:shadow-xl hover:-translate-y-0.5 transition-all active:scale-95 flex items-center gap-3">
<span class="material-symbols-outlined">check_circle</span>
                Konfirmasi Pilihan Paket
            </button>
</div>
</section>
<!-- 4. Website Skeleton Template Chooser -->
<section class="flex flex-col gap-8">
<div class="text-center">
<h3 class="font-headline-md text-display-lg-mobile text-on-surface mb-2">Pilih Struktur Template</h3>
<p class="text-on-surface-variant font-body-md">Pilih salah satu dari 9 wireframe dasar untuk memulai generasi visual.</p>
</div>
<div class="grid grid-cols-1 md:grid-cols-3 gap-6">
<!-- 9 Skeleton Templates -->
<div class="skeleton-card bg-surface-container-lowest border-2 border-outline-variant rounded-xl p-5 cursor-pointer hover:border-primary/50 transition-all flex flex-col gap-4 group selected">
<div class="bg-surface-container-low h-32 rounded-lg relative overflow-hidden flex flex-col gap-2 p-3">
<div class="h-3 w-1/2 bg-outline-variant rounded"></div>
<div class="flex gap-2">
<div class="h-16 flex-grow bg-outline-variant/30 rounded"></div>
<div class="h-16 w-1/3 bg-outline-variant/30 rounded"></div>
</div>
</div>
<div class="flex items-center justify-between">
<span class="font-bold text-on-surface">Modern Agency</span>
<span class="material-symbols-outlined text-primary opacity-0 group-[.selected]:opacity-100">check_circle</span>
</div>
</div>
<div class="skeleton-card bg-surface-container-lowest border-2 border-outline-variant rounded-xl p-5 cursor-pointer hover:border-primary/50 transition-all flex flex-col gap-4 group">
<div class="bg-surface-container-low h-32 rounded-lg relative overflow-hidden flex flex-col gap-2 p-3">
<div class="h-3 w-3/4 mx-auto bg-outline-variant rounded"></div>
<div class="grid grid-cols-2 gap-2 h-16 mt-2">
<div class="bg-outline-variant/30 rounded"></div>
<div class="bg-outline-variant/30 rounded"></div>
</div>
</div>
<span class="font-bold text-on-surface">Minimal Portfolio</span>
</div>
<div class="skeleton-card bg-surface-container-lowest border-2 border-outline-variant rounded-xl p-5 cursor-pointer hover:border-primary/50 transition-all flex flex-col gap-4 group">
<div class="bg-surface-container-low h-32 rounded-lg relative overflow-hidden flex flex-col gap-2 p-3">
<div class="h-8 w-full bg-outline-variant rounded"></div>
<div class="h-12 w-full bg-outline-variant/30 rounded mt-1"></div>
</div>
<span class="font-bold text-on-surface">Corporate Landing</span>
</div>
<div class="skeleton-card bg-surface-container-lowest border-2 border-outline-variant rounded-xl p-5 cursor-pointer hover:border-primary/50 transition-all flex flex-col gap-4 group">
<div class="bg-surface-container-low h-32 rounded-lg relative overflow-hidden flex p-2 gap-2">
<div class="w-8 bg-outline-variant rounded"></div>
<div class="flex-grow flex flex-col gap-2">
<div class="h-3 w-full bg-outline-variant rounded"></div>
<div class="flex-grow bg-outline-variant/30 rounded"></div>
</div>
</div>
<span class="font-bold text-on-surface">Dashboard Sidebar</span>
</div>
<div class="skeleton-card bg-surface-container-lowest border-2 border-outline-variant rounded-xl p-5 cursor-pointer hover:border-primary/50 transition-all flex flex-col gap-4 group">
<div class="bg-surface-container-low h-32 rounded-lg relative overflow-hidden grid grid-cols-3 gap-2 p-3">
<div class="bg-outline-variant/30 rounded"></div>
<div class="bg-outline-variant/30 rounded"></div>
<div class="bg-outline-variant/30 rounded"></div>
<div class="bg-outline-variant/30 rounded"></div>
<div class="bg-outline-variant/30 rounded"></div>
<div class="bg-outline-variant/30 rounded"></div>
</div>
<span class="font-bold text-on-surface">E-Commerce Grid</span>
</div>
<div class="skeleton-card bg-surface-container-lowest border-2 border-outline-variant rounded-xl p-5 cursor-pointer hover:border-primary/50 transition-all flex flex-col gap-4 group">
<div class="bg-surface-container-low h-32 rounded-lg relative overflow-hidden flex flex-col gap-2 p-3 items-center">
<div class="w-10 h-10 rounded-full bg-outline-variant"></div>
<div class="h-3 w-3/4 bg-outline-variant rounded"></div>
<div class="h-3 w-1/2 bg-outline-variant rounded"></div>
</div>
<span class="font-bold text-on-surface">Personal Brand</span>
</div>
<div class="skeleton-card bg-surface-container-lowest border-2 border-outline-variant rounded-xl p-5 cursor-pointer hover:border-primary/50 transition-all flex flex-col gap-4 group">
<div class="bg-surface-container-low h-32 rounded-lg relative overflow-hidden flex flex-col gap-1 p-3">
<div class="h-2 w-full bg-outline-variant rounded"></div>
<div class="h-20 w-full bg-outline-variant/30 rounded"></div>
<div class="flex gap-1">
<div class="h-4 w-4 bg-outline-variant rounded-full"></div>
<div class="h-4 w-4 bg-outline-variant rounded-full"></div>
</div>
</div>
<span class="font-bold text-on-surface">Blog Article</span>
</div>
<div class="skeleton-card bg-surface-container-lowest border-2 border-outline-variant rounded-xl p-5 cursor-pointer hover:border-primary/50 transition-all flex flex-col gap-4 group">
<div class="bg-surface-container-low h-32 rounded-lg relative overflow-hidden p-3 flex flex-col gap-3">
<div class="flex justify-between items-center">
<div class="h-3 w-1/4 bg-outline-variant rounded"></div>
<div class="h-3 w-1/4 bg-outline-variant rounded"></div>
</div>
<div class="h-16 w-full bg-outline-variant/30 rounded"></div>
</div>
<span class="font-bold text-on-surface">SaaS Landing</span>
</div>
<div class="skeleton-card bg-surface-container-lowest border-2 border-outline-variant rounded-xl p-5 cursor-pointer hover:border-primary/50 transition-all flex flex-col gap-4 group">
<div class="bg-surface-container-low h-32 rounded-lg relative overflow-hidden p-3 flex gap-2">
<div class="w-1/2 bg-outline-variant/30 rounded"></div>
<div class="w-1/2 flex flex-col gap-2">
<div class="h-3 w-full bg-outline-variant rounded"></div>
<div class="h-3 w-full bg-outline-variant rounded"></div>
<div class="h-8 w-full bg-primary/20 rounded"></div>
</div>
</div>
<span class="font-bold text-on-surface">Event RSVP</span>
</div>
</div>
<div class="mt-8 p-8 bg-primary/5 border border-primary/20 rounded-2xl text-center">
<p class="font-body-md text-on-surface-variant mb-6">Siap untuk melihat hasil website Anda?</p>
<button class="bg-primary text-on-primary px-16 py-5 rounded-full font-headline-md text-xl shadow-lg hover:shadow-primary/30 hover:scale-105 transition-all">
                Mulai Generate Website ✨
            </button>
</div>
</section>
</main>
<!-- Footer Component -->
<footer class="w-full mt-24 bg-surface-container-low border-t border-outline-variant">
<div class="flex flex-col md:flex-row justify-between items-center py-8 px-margin-desktop max-w-container-max mx-auto">
<div class="flex items-center gap-2 mb-4 md:mb-0">
<span class="text-body-lg font-headline-md font-semibold text-on-surface">AIGenius Builder</span>
<span class="text-on-surface-variant font-body-md opacity-60">| © 2024. All rights reserved.</span>
</div>
<div class="flex gap-gutter">
<a class="font-label-caps text-label-caps text-on-surface-variant hover:text-primary transition-colors" href="#">Privacy Policy</a>
<a class="font-label-caps text-label-caps text-on-surface-variant hover:text-primary transition-colors" href="#">Terms of Service</a>
<a class="font-label-caps text-label-caps text-on-surface-variant hover:text-primary transition-colors" href="#">API Docs</a>
<a class="font-label-caps text-label-caps text-on-surface-variant hover:text-primary transition-colors" href="#">Support</a>
</div>
</div>
</footer>
<script>
    // Selection logic for skeleton templates
    const cards = document.querySelectorAll('.skeleton-card');
    cards.forEach(card => {
        card.addEventListener('click', () => {
            cards.forEach(c => {
                c.classList.remove('selected');
                const check = c.querySelector('.material-symbols-outlined');
                if (check) check.remove();
            });
            card.classList.add('selected');
            const titleContainer = card.querySelector('div:last-child');
            if (titleContainer && !titleContainer.querySelector('.material-symbols-outlined')) {
                const checkIcon = document.createElement('span');
                checkIcon.className = 'material-symbols-outlined text-primary';
                checkIcon.innerText = 'check_circle';
                titleContainer.appendChild(checkIcon);
            }
        });
    });

    // Row selection for product table
    const tableRows = document.querySelectorAll('tbody tr');
    tableRows.forEach(row => {
        row.addEventListener('click', () => {
            const radio = row.querySelector('input[type="radio"]');
            if (radio) radio.checked = true;
        });
    });
</script>
</body></html>

<!-- Preview & Deploy Website -->
<!DOCTYPE html><html class="light" lang="id" style=""><head>
<meta charset="utf-8">
<meta content="width=device-width, initial-scale=1.0" name="viewport">
<title>AIGenius - Preview &amp; Deploy</title>
<script src="https://cdn.tailwindcss.com?plugins=forms,container-queries"></script>
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700&amp;family=JetBrains+Mono&amp;display=swap" rel="stylesheet">
<link href="https://fonts.googleapis.com/css2?family=Material+Symbols+Outlined:wght,FILL@100..700,0..1&amp;display=swap" rel="stylesheet">
<link href="https://fonts.googleapis.com/css2?family=Material+Symbols+Outlined:wght,FILL@100..700,0..1&amp;display=swap" rel="stylesheet">
<!-- Tailwind Configuration -->
<script id="tailwind-config">
      tailwind.config = {
        darkMode: "class",
        theme: {
          extend: {
            "colors": {
                    "surface-container-highest": "#d3e4fe",
                    "on-secondary-container": "#004666",
                    "surface-dim": "#cbdbf5",
                    "outline-variant": "#c7c4d8",
                    "surface-variant": "#d3e4fe",
                    "on-secondary-fixed-variant": "#004c6e",
                    "on-surface-variant": "#464555",
                    "primary-fixed": "#e2dfff",
                    "on-primary-fixed": "#0f0069",
                    "background": "#f8f9ff",
                    "surface-container-lowest": "#ffffff",
                    "on-secondary": "#ffffff",
                    "surface-container-high": "#dce9ff",
                    "on-primary-container": "#dad7ff",
                    "outline": "#777587",
                    "on-background": "#0b1c30",
                    "secondary-fixed-dim": "#89ceff",
                    "error-container": "#ffdad6",
                    "on-tertiary-container": "#ffd0d2",
                    "inverse-surface": "#213145",
                    "primary-fixed-dim": "#c3c0ff",
                    "on-tertiary-fixed-variant": "#92002a",
                    "secondary-fixed": "#c9e6ff",
                    "surface-bright": "#f8f9ff",
                    "inverse-primary": "#c3c0ff",
                    "on-tertiary": "#ffffff",
                    "tertiary-fixed": "#ffdadb",
                    "primary": "#3525cd",
                    "surface-container-low": "#eff4ff",
                    "tertiary-container": "#bf0f3c",
                    "inverse-on-surface": "#eaf1ff",
                    "surface-tint": "#4d44e3",
                    "on-primary": "#ffffff",
                    "secondary-container": "#39b8fd",
                    "on-secondary-fixed": "#001e2f",
                    "tertiary": "#95002b",
                    "on-tertiary-fixed": "#40000d",
                    "error": "#ba1a1a",
                    "secondary": "#006591",
                    "on-surface": "#0b1c30",
                    "surface": "#f8f9ff",
                    "primary-container": "#4f46e5",
                    "tertiary-fixed-dim": "#ffb2b7",
                    "on-primary-fixed-variant": "#3323cc",
                    "on-error-container": "#93000a",
                    "on-error": "#ffffff",
                    "surface-container": "#e5eeff"
            },
            "borderRadius": {
                    "DEFAULT": "0.25rem",
                    "lg": "0.5rem",
                    "xl": "0.75rem",
                    "full": "9999px"
            },
            "spacing": {
                    "margin-desktop": "48px",
                    "container-max": "1280px",
                    "margin-mobile": "16px",
                    "gutter": "24px",
                    "base": "8px"
            },
            "fontFamily": {
                    "headline-md": ["Inter"],
                    "code-sm": ["JetBrains Mono"],
                    "body-lg": ["Inter"],
                    "display-lg": ["Inter"],
                    "label-caps": ["Inter"],
                    "display-lg-mobile": ["Inter"],
                    "body-md": ["Inter"]
            },
            "fontSize": {
                    "headline-md": ["24px", {"lineHeight": "32px", "fontWeight": "600"}],
                    "code-sm": ["14px", {"lineHeight": "20px", "fontWeight": "400"}],
                    "body-lg": ["18px", {"lineHeight": "28px", "fontWeight": "400"}],
                    "display-lg": ["48px", {"lineHeight": "56px", "letterSpacing": "-0.02em", "fontWeight": "700"}],
                    "label-caps": ["12px", {"lineHeight": "16px", "letterSpacing": "0.05em", "fontWeight": "600"}],
                    "display-lg-mobile": ["32px", {"lineHeight": "40px", "letterSpacing": "-0.01em", "fontWeight": "700"}],
                    "body-md": ["16px", {"lineHeight": "24px", "fontWeight": "400"}]
            }
          },
        },
      }
    </script>
<style>
        .glass-effect {
            backdrop-filter: blur(10px);
            background: rgba(255, 255, 255, 0.7);
        }
        .preview-iframe-container {
            box-shadow: 0 10px 40px -10px rgba(11, 28, 48, 0.15);
        }
        .chat-glow {
            box-shadow: 0 0 20px rgba(79, 70, 229, 0.1);
        }
    </style>
</head>
<body class="bg-background text-on-surface font-body-md text-body-md min-h-screen flex flex-col overflow-x-hidden">
<!-- TopNavBar -->
<header class="w-full top-0 sticky bg-surface-container-lowest dark:bg-surface-dim shadow-sm z-50">
<nav class="flex justify-between items-center h-16 px-margin-desktop max-w-container-max mx-auto">
<div class="flex items-center gap-8">
<span class="text-headline-md font-headline-md font-bold text-primary dark:text-primary-fixed">AIGenius</span>
<div class="hidden md:flex gap-6 items-center">
<a class="font-label-caps text-label-caps text-on-surface-variant dark:text-outline-variant hover:text-primary transition-colors" href="#">Dashboard</a>
<a class="font-label-caps text-label-caps text-primary dark:text-primary-fixed-dim border-b-2 border-primary dark:border-primary-fixed-dim pb-1" href="#">Projects</a>

<a class="font-label-caps text-label-caps text-on-surface-variant dark:text-outline-variant hover:text-primary transition-colors" href="#">Billing</a>
</div>
</div>
<div class="flex items-center gap-4">
<button class="font-label-caps text-label-caps text-on-surface-variant hover:bg-surface-container-low px-4 py-2 rounded transition-all active:scale-95">Help</button>
<button class="font-label-caps text-label-caps bg-primary-container text-on-primary-container px-6 py-2 rounded-full font-semibold transition-all hover:bg-opacity-90 active:scale-95">Deploy</button>
<img alt="User Profile Avatar" class="w-8 h-8 rounded-full border border-outline-variant" src="https://lh3.googleusercontent.com/aida-public/AB6AXuAa1j_FStpt2bEF0QcUDYCXtiRYfn_rcTmA0YOVZ6KIF7dW3PdNKuSXDceOgX-UIL7wXNV7LKQ-7DgWYGO0WRrhvGU9zf_linSWCqnHcPf1kYR1ggjOBCfNc07ciyp8jSOwYLOtUKdG5gr84jkL8MHwVT2S3UmZWUxhNUkfx_fEcIyqExX1Rq_amrG4NwlGGUbLjtKbrY3VErjijo0w1AV-paY--hESPCTHAtiDSBsi9aJZz2wX-Gum8jz4yi9IPfBYc3slP5cxj3c">
</div>
</nav>
</header>
<main class="flex-grow flex flex-col lg:flex-row w-full max-w-container-max mx-auto px-margin-mobile md:px-margin-desktop py-8 gap-8 overflow-hidden">
<!-- Left Section: Preview Website -->
<section class="flex-grow flex flex-col gap-6">
<div class="flex justify-between items-center">
<h1 class="font-headline-md text-headline-md text-on-background">Pratinjau Situs Web</h1>
<div class="flex bg-surface-container-high p-1 rounded-lg">
<button class="p-2 bg-white rounded-md shadow-sm text-primary flex items-center">
<span class="material-symbols-outlined text-sm">desktop_windows</span>
</button>
<button class="p-2 text-on-surface-variant flex items-center hover:bg-surface-variant rounded-md transition-colors">
<span class="material-symbols-outlined text-sm">tablet</span>
</button>
<button class="p-2 text-on-surface-variant flex items-center hover:bg-surface-variant rounded-md transition-colors">
<span class="material-symbols-outlined text-sm">smartphone</span>
</button>
</div>
</div>
<div class="preview-iframe-container bg-white border border-outline-variant rounded-xl overflow-hidden flex-grow min-h-[500px] relative">
<!-- Browser Header Decor -->
<div class="bg-surface-container h-10 flex items-center px-4 gap-2 border-b border-outline-variant">
<div class="flex gap-1.5">
<div class="w-3 h-3 rounded-full bg-error/40"></div>
<div class="w-3 h-3 rounded-full bg-secondary-container/40"></div>
<div class="w-3 h-3 rounded-full bg-surface-dim"></div>
</div>
<div class="mx-auto bg-surface-container-lowest px-4 py-0.5 rounded-md text-[10px] text-outline border border-outline-variant w-1/3 text-center">
                        https://project-aigenius-72.builder.app
                    </div>
</div>
<!-- Site Content Simulation -->
<div class="w-full h-full overflow-y-auto bg-slate-50 relative group">
<div class="absolute inset-0 bg-gradient-to-tr from-primary/5 via-transparent to-secondary/5 pointer-events-none"></div>
<!-- Content Placeholder Area -->
<div class="p-12 space-y-12">
<!-- Hero Section Preview -->
<div class="max-w-3xl mx-auto text-center space-y-6">
<div class="h-4 w-32 bg-primary/20 rounded-full mx-auto animate-pulse"></div>
<div class="h-12 bg-on-background/10 rounded-lg w-full"></div>
<div class="h-6 bg-on-background/5 rounded-lg w-3/4 mx-auto"></div>
<div class="flex justify-center gap-4 pt-4">
<div class="h-12 w-40 bg-primary rounded-lg"></div>
<div class="h-12 w-40 border-2 border-outline-variant rounded-lg"></div>
</div>
</div>
<!-- Grid Section Preview -->
<div class="grid grid-cols-1 md:grid-cols-3 gap-6">
<div class="h-64 bg-white border border-outline-variant rounded-2xl shadow-sm p-6 space-y-4">
<div class="w-12 h-12 bg-secondary-container/20 rounded-xl"></div>
<div class="h-6 w-1/2 bg-on-surface/10 rounded-md"></div>
<div class="h-20 w-full bg-on-surface/5 rounded-md"></div>
</div>
<div class="h-64 bg-white border border-outline-variant rounded-2xl shadow-sm p-6 space-y-4">
<div class="w-12 h-12 bg-primary/20 rounded-xl"></div>
<div class="h-6 w-1/2 bg-on-surface/10 rounded-md"></div>
<div class="h-20 w-full bg-on-surface/5 rounded-md"></div>
</div>
<div class="h-64 bg-white border border-outline-variant rounded-2xl shadow-sm p-6 space-y-4">
<div class="w-12 h-12 bg-tertiary-fixed/30 rounded-xl"></div>
<div class="h-6 w-1/2 bg-on-surface/10 rounded-md"></div>
<div class="h-20 w-full bg-on-surface/5 rounded-md"></div>
</div>
</div>
</div>
<!-- Watermark -->
<div class="absolute bottom-4 right-4 flex items-center gap-2 px-3 py-1.5 bg-white/80 backdrop-blur-md rounded-full border border-outline-variant shadow-sm opacity-0 group-hover:opacity-100 transition-opacity">
<span class="text-[10px] font-semibold text-on-surface-variant">BUILT WITH</span>
<span class="text-[10px] font-bold text-primary">AIGenius</span>
</div>
</div>
</div>
</section>
<!-- Right Section: Sidebar -->
<aside class="w-full lg:w-96 flex flex-col gap-6">
<!-- Chatbox Revisi -->
<div class="bg-surface-container-lowest border border-outline-variant rounded-2xl flex flex-col h-[450px] chat-glow">
<div class="p-4 border-b border-outline-variant flex items-center justify-between">
<div class="flex items-center gap-2">
<span class="material-symbols-outlined text-primary" data-weight="fill">auto_awesome</span>
<span class="font-semibold text-on-background">Revisi Website</span>
</div>
<span class="w-2 h-2 rounded-full bg-emerald-500 animate-pulse"></span>
</div>
<div class="flex-grow p-4 overflow-y-auto space-y-4 scroll-smooth">
<div class="flex flex-col gap-1 max-w-[85%]">
<div class="bg-surface-container p-3 rounded-2xl rounded-tl-none text-on-surface-variant text-sm">
                            Halo! Saya AIGenius. Apa ada bagian dari desain atau konten yang ingin Anda revisi?
                        </div>
<span class="text-[10px] text-outline ml-1">10:24 AM</span>
</div>
<div class="flex flex-col gap-1 items-end ml-auto max-w-[85%]">
<div class="bg-primary text-white p-3 rounded-2xl rounded-tr-none text-sm shadow-sm">
                            Ubah warna aksen menjadi biru laut dan tambahkan bagian testimoni di bawah hero.
                        </div>
<span class="text-[10px] text-outline mr-1">10:25 AM</span>
</div>
<div class="flex flex-col gap-1 max-w-[85%]">
<div class="bg-surface-container p-3 rounded-2xl rounded-tl-none text-on-surface-variant text-sm flex items-center gap-3">
<div class="flex space-x-1">
<div class="w-1.5 h-1.5 bg-primary/40 rounded-full animate-bounce"></div>
<div class="w-1.5 h-1.5 bg-primary/40 rounded-full animate-bounce [animation-delay:0.2s]"></div>
<div class="w-1.5 h-1.5 bg-primary/40 rounded-full animate-bounce [animation-delay:0.4s]"></div>
</div>
                            Sedang memproses perubahan visual...
                        </div>
</div>
</div>
<div class="p-4 pt-0">
<div class="relative">
<textarea class="w-full bg-surface-container-low border border-outline-variant rounded-xl p-3 pr-12 text-sm focus:ring-2 focus:ring-primary focus:border-transparent transition-all outline-none resize-none" placeholder="Ketik permintaan revisi..." rows="2"></textarea>
<button class="absolute right-3 bottom-3 p-2 bg-primary text-white rounded-lg active:scale-90 transition-transform">
<span class="material-symbols-outlined text-sm">send</span>
</button>
</div>
<p class="text-[10px] text-outline mt-2 text-center">AI akan langsung memperbarui pratinjau di sebelah kiri.</p>
</div>
</div>
<!-- Detail Deployment -->
<div class="bg-white border border-outline-variant rounded-2xl p-6 space-y-6 shadow-sm">
<h2 class="font-semibold text-on-background flex items-center gap-2">
<span class="material-symbols-outlined text-secondary">cloud_upload</span>
                    Detail Deployment
                </h2>
<div class="space-y-4">
<div class="flex justify-between items-start">
<div>
<p class="font-semibold text-sm">Biaya Hosting &amp; Domain</p>
<p class="text-[10px] text-outline">Paket Professional (Tahunan)</p>
</div>
<div class="text-right">
<p class="font-bold text-primary">Rp 1.250.000</p>
<p class="text-[10px] text-outline">/tahun</p>
</div>
</div>
<div class="bg-surface-container-lowest border border-outline-variant rounded-xl p-3 space-y-2">
<div class="flex justify-between text-xs">
<span class="text-on-surface-variant">Cloud Hosting 10GB</span>
<span class="text-on-surface font-semibold">Aktif</span>
</div>
<div class="flex justify-between text-xs">
<span class="text-on-surface-variant">SSL Certificate</span>
<span class="text-on-surface font-semibold">Gratis</span>
</div>
<div class="flex justify-between text-xs">
<span class="text-on-surface-variant">Custom Domain (.com)</span>
<span class="text-on-surface font-semibold">Tersedia</span>
</div>
</div>
</div>
<div class="pt-2">
<button class="w-full bg-primary-container text-on-primary-container py-4 rounded-xl font-bold flex items-center justify-center gap-3 hover:shadow-lg transition-all active:scale-[0.98] group relative overflow-hidden">

<span class="relative z-10">Deploy Website</span>
<span class="material-symbols-outlined relative z-10 group-hover:translate-x-1 transition-transform">rocket_launch</span>
</button>
<p class="text-center text-[10px] text-outline mt-3">Dengan klik Deploy, situs Anda akan online dalam <span class="font-bold">~2 menit</span>.</p>
</div>
</div>
</aside>
</main>
<!-- Footer -->
<footer class="w-full mt-auto bg-surface-container-low dark:bg-on-background border-t border-outline-variant dark:border-outline">
<div class="flex flex-col md:flex-row justify-between items-center py-base px-margin-desktop max-w-container-max mx-auto h-16 md:h-20">
<div class="flex items-center gap-2">
<span class="text-body-lg font-headline-md font-semibold text-on-surface dark:text-inverse-on-surface">AIGenius</span>
<span class="text-xs text-outline-variant">v2.4.0</span>
</div>
<p class="font-body-md text-label-caps text-on-surface-variant dark:text-outline-variant mt-2 md:mt-0">© 2024 AIGenius Builder. All rights reserved.</p>
<div class="flex gap-6 mt-2 md:mt-0">
<a class="font-label-caps text-label-caps text-on-surface-variant dark:text-outline-variant hover:text-primary transition-colors" href="#">Privacy Policy</a>
<a class="font-label-caps text-label-caps text-on-surface-variant dark:text-outline-variant hover:text-primary transition-colors" href="#">Terms of Service</a>
<a class="font-label-caps text-label-caps text-on-surface-variant dark:text-outline-variant hover:text-primary transition-colors" href="#">Support</a>
</div>
</div>
</footer>
<!-- Atmosphere/Interactions Script -->
<script>
        // Simulate real-time interaction for the chat and preview
        document.addEventListener('DOMContentLoaded', () => {
            const textarea = document.querySelector('textarea');
            const chatContainer = document.querySelector('.overflow-y-auto.space-y-4');
            
            // Subtle hover effect for the main preview
            const preview = document.querySelector('.preview-iframe-container');
            preview.addEventListener('mousemove', (e) => {
                const rect = preview.getBoundingClientRect();
                const x = e.clientX - rect.left;
                const y = e.clientY - rect.top;
                preview.style.setProperty('--mouse-x', `${x}px`);
                preview.style.setProperty('--mouse-y', `${y}px`);
            });
        });
    </script>
</body></html>