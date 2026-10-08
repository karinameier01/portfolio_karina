<template>
  <div class="portfolio-page">
    <header class="site-header">
      <div class="brand-block">
        <span class="brand-mark">KARINA MEIER</span>
      </div>

      <nav class="main-nav" aria-label="Navegação principal">
        <button v-for="item in navItems" :key="item.id" type="button" class="nav-link" @click="scrollToSection(item.id)">
          {{ item.label }}
        </button>
      </nav>
    </header>

    <main class="page-content">
      <section id="inicio" class="hero reveal">
        <div class="hero-copy">
          <p class="eyebrow">Estudante de Tecnologia</p>
          <h1>KARINA MEIER</h1>
          <p class="hero-tagline">Tecnologia, criatividade e desenvolvimento de software.</p>

          <div class="hero-meta">
            <span>Joinville — SC</span>
            <span>Estudante de Tecnologia</span>
            <span>2024 — 2026</span>
          </div>

          <div class="cta-row">
            <button type="button" class="button primary" @click="scrollToSection('projetos')">Ver projetos</button>
            <button type="button" class="button secondary" @click="scrollToSection('sobre')">Sobre mim</button>
          </div>
        </div>

        <div class="hero-visual" aria-hidden="true">
          <div class="visual-frame">
            <div class="visual-label">TRAJETÓRIA</div>
            <div class="visual-grid">
              <span>HTML</span>
              <span>CSS</span>
              <span>JS</span>
              <span>Vue</span>
              <span>Ionic</span>
              <span>PHP</span>
              <span>SQL</span>
              <span>C++</span>
            </div>
            <div class="vertical-line"></div>
          </div>
        </div>
      </section>

      <div class="scroll-cue">Scroll para explorar</div>

      <section id="sobre" class="story-section reveal">
        <div class="section-number">01</div>
        <div class="section-copy">
          <p class="eyebrow">Sobre mim</p>
          <h2>Estudante de tecnologia, construindo conhecimento através de prática.</h2>
          <p>
            Sou estudante do curso Técnico em Informática para Internet no SENAC, com formação prevista para dezembro de 2026.
            Meu interesse está em desenvolvimento de software, programação, desenvolvimento de sistemas, tecnologia e resolução de problemas.
          </p>
          <p>
            Meu objetivo profissional é buscar uma oportunidade de estágio na área de Tecnologia da Informação, continuar aprendendo
            com projetos reais e construir uma base sólida para minha carreira em desenvolvimento.
          </p>
        </div>
      </section>

      <section class="impact-quote reveal">
        <p>Não comecei sabendo criar sistemas. Comecei querendo entender como eles funcionavam.</p>
      </section>

      <section id="trajetoria" class="timeline-section reveal">
        <div class="section-header">
          <p class="eyebrow">Minha trajetória</p>
          <h2>Do primeiro contato com tecnologia ao caminho em desenvolvimento.</h2>
        </div>

        <div class="timeline">
          <article v-for="item in timeline" :key="item.year" class="timeline-item">
            <div class="timeline-year">{{ item.year }}</div>
            <div class="timeline-content">
              <h3>{{ item.title }}</h3>
              <p>{{ item.text }}</p>
            </div>
          </article>
        </div>
      </section>

      <section id="meninas" class="feature-split reveal">
        <div class="feature-intro">
          <p class="eyebrow">Meninas na Tecnologia</p>
          <h2>Um primeiro contato direto com a prática e a criação.</h2>
        </div>

        <div class="feature-evolution">
          <div class="evolution-column">
            <span class="small-label">2024</span>
            <p>Primeiro contato com programação, C++, Arduino, robótica, eletrônica e protótipos.</p>
          </div>
          <div class="evolution-arrow" aria-hidden="true">↓</div>
          <div class="evolution-column">
            <span class="small-label">2026</span>
            <p>Continuidade e evolução no projeto, com mais maturidade no trabalho em equipe, no desenvolvimento e na criação de soluções.</p>
          </div>
        </div>

        <div class="feature-grid">
          <div class="feature-box">
            <span class="small-label">Projeto</span>
            <p>Promovido pela UFSC em parceria com o SENAC.</p>
          </div>
          <div class="feature-box">
            <span class="small-label">Aprendizados</span>
            <p>Programação, robótica, prototipagem, trabalho em equipe e participação em desafios práticos.</p>
          </div>
          <div class="feature-box highlight">
            <span class="small-label">Reconhecimento</span>
            <p>3º lugar na etapa final em 2024.</p>
          </div>
        </div>
      </section>

      <section id="jedi" class="jedi-section reveal">
        <div class="section-number">02</div>
        <div class="section-copy">
          <p class="eyebrow">16ª edição do JEDI</p>
          <h2>Empreendedorismo, inovação e apresentação de ideias com foco em soluções reais.</h2>
          <p>
            Em 2026, participei da 16ª edição do JEDI, programa promovido pelo Join.Valle e Sebrae, com apoio do Ágora Tech Park.
            A experiência foi importante para entender como ideias ganham forma, como se trabalha em equipe e como validar soluções para problemas reais.
          </p>
        </div>
      </section>

      <section id="projetos" class="projects-section reveal">
        <div class="section-header inline-header">
          <div>
            <p class="eyebrow">Projetos</p>
            <h2>Algumas das coisas que construí enquanto aprendia.</h2>
          </div>
          <p class="section-copy-mini">Projetos reais, em desenvolvimento e em evolução.</p>
        </div>

        <div class="project-layout">
          <article v-for="project in projects" :key="project.id" :class="['project-card', project.size]" @click="openProject(project)">
            <div class="project-visual" :style="project.visualStyle">
              <span class="project-index">{{ project.index }}</span>
              <div class="mini-grid">
                <span v-for="word in project.previewWords" :key="word">{{ word }}</span>
              </div>
            </div>
            <div class="project-content">
              <div class="project-topline">
                <span>{{ project.type }}</span>
                <span>{{ project.year }}</span>
              </div>
              <h3>{{ project.title }}</h3>
              <p>{{ project.summary }}</p>
              <div class="chip-row">
                <span v-for="tech in project.techs.slice(0, 3)" :key="tech" class="chip">{{ tech }}</span>
              </div>
            </div>
          </article>
        </div>
      </section>

      <section id="habilidades" class="skills-section reveal">
        <div class="section-header">
          <p class="eyebrow">Habilidades</p>
          <h2>Conhecimentos em constante construção.</h2>
        </div>

        <div class="skills-grid">
          <article v-for="group in skillGroups" :key="group.title" class="skill-block">
            <h3>{{ group.title }}</h3>
            <ul>
              <li v-for="item in group.items" :key="item">{{ item }}</li>
            </ul>
          </article>
        </div>
      </section>

      <section class="soft-skills reveal">
        <div class="section-header compact">
          <p class="eyebrow">Além do código</p>
          <h2>Valorizo colaboração, comunicação e resolução de problemas.</h2>
        </div>

        <div class="soft-list">
          <span>Trabalho em equipe</span>
          <span>Comunicação</span>
          <span>Resolução de problemas</span>
          <span>Aprendizado contínuo</span>
        </div>
      </section>

      <section id="curriculo" class="resume-section reveal">
        <div class="section-number">03</div>
        <div class="section-copy">
          <p class="eyebrow">Currículo</p>
          <h2>Formação, cursos e atividades que me ajudaram a construir a base da minha trajetória.</h2>

          <div class="resume-list">
            <div class="resume-item">
              <span class="resume-label">Formação</span>
              <strong>Técnico em Informática para Internet</strong>
              <p>SENAC · 2024 — 2026</p>
            </div>
            <div class="resume-item">
              <span class="resume-label">Cursos</span>
              <strong>Excel Básico</strong>
              <p>SENAI · 20h</p>
            </div>
            <div class="resume-item">
              <span class="resume-label">Cursos</span>
              <strong>Introdução à Programação</strong>
              <p>SENAI · 10h</p>
            </div>
            <div class="resume-item">
              <span class="resume-label">Cursos</span>
              <strong>Introdução aos Jogos Digitais</strong>
              <p>SENAI</p>
            </div>
            <div class="resume-item highlight-item">
              <span class="resume-label">Atividades</span>
              <strong>Meninas na Tecnologia</strong>
              <p>JEDI · projetos acadêmicos e extracurriculares</p>
            </div>
          </div>

          <a href="/karina-curriculo.txt" class="button primary" download>Baixar currículo</a>
        </div>
      </section>

      <section id="github" class="github-section reveal">
        <div class="section-header inline-header">
          <div>
            <p class="eyebrow">Meu código</p>
            <h2>Projetos, experimentos e aprendizados registrados no GitHub.</h2>
          </div>
          <div class="github-links">
            <a class="button secondary" href="https://github.com/karinameier01" target="_blank" rel="noreferrer">GitHub principal</a>
            <a class="button secondary" href="https://github.com/itszkaah?tab=repositories" target="_blank" rel="noreferrer">Conta extra</a>
          </div>
        </div>

        <div class="repo-grid">
          <article v-for="repo in githubRepos" :key="repo.name" class="repo-card">
            <div class="repo-topline">
              <h3>{{ repo.name }}</h3>
              <span>{{ repo.language || 'Diversos' }}</span>
            </div>
            <p>{{ repo.description || 'Projeto em desenvolvimento.' }}</p>
            <a :href="repo.url" target="_blank" rel="noreferrer">Acessar repositório</a>
          </article>
        </div>
      </section>

      <section class="profile-cta reveal">
        <div class="cta-copy">
          <p class="eyebrow">Minha trajetória profissional</p>
          <h2>Para acompanhar minha evolução e conhecer mais sobre meu percurso em tecnologia.</h2>
        </div>
        <a class="button primary" href="https://www.linkedin.com/in/karina-meier-69aba3368/" target="_blank" rel="noreferrer">Ver LinkedIn</a>
      </section>

      <section id="contatos" class="contact-section reveal">
        <p class="eyebrow">Contato</p>
        <h2>Vamos conversar.</h2>
        <p>
          Estou em busca de oportunidades para continuar aprendendo, desenvolver minhas habilidades e contribuir com projetos reais em tecnologia.
        </p>

        <div class="contact-grid">
          <a href="mailto:karinameier28@gmail.com" class="contact-card">karinameier28@gmail.com</a>
          <span class="contact-card">Joinville — SC</span>
          <a href="https://www.linkedin.com/in/karina-meier-69aba3368/" target="_blank" rel="noreferrer" class="contact-card">LinkedIn</a>
          <a href="https://github.com/karinameier01" target="_blank" rel="noreferrer" class="contact-card">GitHub</a>
        </div>
      </section>
    </main>

    <footer class="site-footer">
      <p>Este é apenas o começo.</p>
      <div class="footer-meta">
        <span>Karina Meier</span>
        <span>Estudante de Tecnologia</span>
        <span>Desenvolvimento de Software</span>
      </div>
      <small>© 2026 Karina Meier</small>
    </footer>

    <div v-if="selectedProject" class="project-modal" role="dialog" aria-modal="true" aria-label="Detalhes do projeto">
      <div class="modal-panel">
        <button type="button" class="modal-close" @click="closeProject" aria-label="Fechar projeto">Fechar</button>
        <div class="modal-header">
          <p class="eyebrow">Projeto</p>
          <h3>{{ selectedProject.title }}</h3>
        </div>

        <div class="modal-body">
          <div class="modal-visual" :style="selectedProject.visualStyle">
            <div class="mini-grid wide-grid">
              <span v-for="word in selectedProject.previewWords" :key="word">{{ word }}</span>
            </div>
          </div>

          <div class="modal-copy">
            <p>{{ selectedProject.description }}</p>
            <div class="detail-group">
              <h4>Objetivo</h4>
              <p>{{ selectedProject.objective }}</p>
            </div>
            <div class="detail-group">
              <h4>Tecnologias</h4>
              <div class="chip-row">
                <span v-for="tech in selectedProject.techs" :key="tech" class="chip">{{ tech }}</span>
              </div>
            </div>
            <div class="detail-group">
              <h4>Minha participação</h4>
              <p>{{ selectedProject.role }}</p>
            </div>
            <a v-if="selectedProject.link" class="button primary" :href="selectedProject.link" target="_blank" rel="noreferrer">Abrir projeto</a>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { onMounted, ref } from 'vue'

const navItems = [
  { id: 'inicio', label: 'Início' },
  { id: 'sobre', label: 'Sobre' },
  { id: 'trajetoria', label: 'Trajetória' },
  { id: 'projetos', label: 'Projetos' },
  { id: 'habilidades', label: 'Habilidades' },
  { id: 'curriculo', label: 'Currículo' },
  { id: 'contatos', label: 'Contatos' },
]

const timeline = [
  {
    year: '2023',
    title: 'Primeiros contatos com tecnologia',
    text: 'Os primeiros cursos profissionalizantes abriram o caminho para entender programação, lógica e o universo da tecnologia.',
  },
  {
    year: '2024',
    title: 'Início do Técnico em Informática',
    text: 'Comecei o curso no SENAC e participei do projeto Meninas na Tecnologia, com foco em programação, C++, Arduino, robótica e eletrônica. Também obtive 3º lugar na etapa final.',
  },
  {
    year: '2025',
    title: 'Evolução e projetos acadêmicos',
    text: 'Aprofundamento dos estudos em programação, desenvolvimento e construção de projetos acadêmicos com foco em solução de problemas.',
  },
  {
    year: '2026',
    title: '3º ano do Técnico e participação no JEDI',
    text: 'Continuação no curso, participação novamente no Meninas na Tecnologia e na 16ª edição do JEDI, com foco em empreendedorismo, inovação e apresentação de ideias.',
  },
]

const projects = [
  {
    id: 'smartevent',
    index: '01',
    title: 'SmartEvent',
    type: 'Aplicativo web',
    year: '2024',
    size: 'large',
    summary: 'Interface para organização visual e apresentação de eventos.',
    description: 'SmartEvent é um projeto desenvolvido em Vue com foco em organização visual e experiência para apresentação de eventos.',
    objective: 'Criar uma interface funcional para apresentar e organizar informações de eventos de forma clara e visualmente agradável.',
    role: 'Criação da interface e estrutura dos componentes, com atenção especial à experiência do usuário.',
    techs: ['Vue', 'TypeScript', 'HTML', 'CSS'],
    link: 'https://github.com/karinameier01/SmartEvent',
    previewWords: ['EVENTO', 'LAYOUT', 'UX', 'UI'],
    visualStyle: { background: 'linear-gradient(135deg, rgba(117,22,45,0.12), rgba(36,33,36,0.08))' },
  },
  {
    id: 'bookiss',
    index: '02',
    title: 'Bookiss',
    type: 'Aplicativo mobile',
    year: '2024',
    size: 'medium',
    summary: 'Aplicativo mobile para explorar livros em interface organizada.',
    description: 'Bookiss é um projeto mobile com foco em catálogo de livros, navegação e organização de conteúdo em telas simples e funcionais.',
    objective: 'Organizar uma experiência de leitura em um ambiente mobile, com foco em usabilidade e navegação clara.',
    role: 'Desenvolvimento da interface e organização visual das páginas e fluxos da aplicação.',
    techs: ['Ionic', 'Vue', 'TypeScript'],
    link: 'https://github.com/karinameier01/Bookiss',
    previewWords: ['CATÁLOGO', 'LISTA', 'LIVROS', 'NAVEGAÇÃO'],
    visualStyle: { background: 'linear-gradient(135deg, rgba(117,22,45,0.14), rgba(242,213,160,0.16))' },
  },
  {
    id: 'albumfig',
    index: '03',
    title: 'AlbumFig',
    type: 'Aplicativo mobile',
    year: '2025',
    size: 'small',
    summary: 'Álbum de figurinhas com login, perfil e coleção.',
    description: 'AlbumFig explora uma experiência de organização visual para coleções, com foco em perfil e navegação em um ambiente móvel.',
    objective: 'Praticar desenvolvimento mobile com organização de conteúdo, fluxo de interação e estrutura visual.',
    role: 'Estrutura do app e visual de interação em telas de cadastro, perfil e coleção.',
    techs: ['Ionic', 'Vue', 'Java'],
    link: 'https://github.com/karinameier01/AlbumFig',
    previewWords: ['COLEÇÃO', 'LOGIN', 'PERFIL', 'APP'],
    visualStyle: { background: 'linear-gradient(135deg, rgba(86,11,24,0.18), rgba(242,229,198,0.18))' },
  },
  {
    id: 'joguinho-burro',
    index: '04',
    title: 'Joguinho Burro',
    type: 'Jogo digital',
    year: '2025',
    size: 'small',
    summary: 'Projeto que explora lógica, interação e apresentação lúdica de um jogo.',
    description: 'Joguinho Burro é um projeto de jogo digital com foco em lógica, interação e experiência de usuário em um ambiente de aprendizagem prática.',
    objective: 'Explorar a lógica de programação em um contexto de jogo, criando uma experiência funcional e envolvente.',
    role: 'Participação no desenvolvimento e organização da interface do projeto.',
    techs: ['JavaScript', 'Vue', 'Ionic'],
    link: 'https://github.com/karinameier01/joguinho_burro',
    previewWords: ['JOGO', 'LÓGICA', 'INTERAÇÃO', 'UI'],
    visualStyle: { background: 'linear-gradient(135deg, rgba(117,22,45,0.12), rgba(242,217,160,0.2))' },
  },
  {
    id: 'meuapp',
    index: '05',
    title: 'meuApp',
    type: 'Estudo em sistemas',
    year: '2025',
    size: 'medium',
    summary: 'Estudo em lógica reativa e composição de interface.',
    description: 'meuApp representa uma prática em desenvolvimento web e organização de lógica reativa em interface com foco em clareza e estrutura.',
    objective: 'Explorar princípios de composição, reatividade e organização de uma aplicação web.',
    role: 'Implementação da estrutura e desenvolvimento da lógica reativa da aplicação.',
    techs: ['Vue', 'TypeScript', 'HTML', 'CSS'],
    link: 'https://github.com/karinameier01/meuApp',
    previewWords: ['VUE', 'LOGICA', 'ESTRUTURA', 'APP'],
    visualStyle: { background: 'linear-gradient(135deg, rgba(36,33,36,0.12), rgba(117,22,45,0.12))' },
  },
  {
    id: 'mini-app',
    index: '06',
    title: 'Mini-App',
    type: 'Experimento front-end',
    year: '2025',
    size: 'large',
    summary: 'Projeto com foco em organização visual, interação e experimentação front-end.',
    description: 'Mini-App é um projeto de estudo em interface e funcionalidade, aplicando conceitos de organização visual e interação para aprendizado prático.',
    objective: 'Experimentar ideias de front-end, estrutura visual e composição em projetos menores.',
    role: 'Participação no desenvolvimento da interface e organização dos elementos de navegação e conteúdo.',
    techs: ['Vue', 'JavaScript', 'CSS'],
    link: 'https://github.com/karinameier01/Mini-App',
    previewWords: ['MINI', 'UI', 'FRONT', 'EXPERIÊNCIA'],
    visualStyle: { background: 'linear-gradient(135deg, rgba(242,229,198,0.22), rgba(117,22,45,0.1))' },
  },
]

const skillGroups = [
  {
    title: 'Desenvolvimento Web',
    items: ['HTML', 'CSS', 'JavaScript', 'Vue'],
  },
  {
    title: 'Desenvolvimento de Aplicações',
    items: ['Ionic', 'Vue', 'Capacitor'],
  },
  {
    title: 'Back-end e Dados',
    items: ['PHP', 'SQL'],
  },
  {
    title: 'Programação e Hardware',
    items: ['C++', 'Arduino', 'Tinkercad', 'Lógica de programação', 'Scratch'],
  },
  {
    title: 'Ferramentas e Organização',
    items: ['Excel', 'Word', 'GitHub'],
  },
]

const fallbackRepos = [
  { name: 'SmartEvent', language: 'Vue', description: 'Interface e experiência de eventos.', url: 'https://github.com/karinameier01/SmartEvent' },
  { name: 'Bookiss', language: 'Ionic', description: 'Aplicativo mobile para consulta e organização de livros.', url: 'https://github.com/karinameier01/Bookiss' },
  { name: 'AlbumFig', language: 'Ionic', description: 'Projeto mobile com organização de coleção e perfil.', url: 'https://github.com/karinameier01/AlbumFig' },
  { name: 'FigAlbum', language: 'Vue', description: 'Projeto de organização visual e de coleção.', url: 'https://github.com/karinameier01/FigAlbum' },
  { name: 'meuApp', language: 'Vue', description: 'Aplicação de estudo em lógica e interface.', url: 'https://github.com/karinameier01/meuApp' },
  { name: 'Joguinho Burro', language: 'JavaScript', description: 'Projeto de jogo e experiência interativa.', url: 'https://github.com/karinameier01/joguinho_burro' },
]

const extraRepos = [
  { name: 'api-geometry', language: 'JavaScript', description: 'API e lógica de geometria com foco em aplicação prática.', url: 'https://github.com/itszkaah/api-geometry' },
  { name: 'api-usuarios', language: 'JavaScript', description: 'Projeto de API para manipulação de usuários e dados.', url: 'https://github.com/itszkaah/api-usuarios' },
  { name: 'formulario', language: 'HTML', description: 'Formulário interativo com estrutura e dinâmica simples.', url: 'https://github.com/itszkaah/formulario' },
  { name: 'ProjetoGrid', language: 'CSS', description: 'Estudo de layout e grid em CSS moderno.', url: 'https://github.com/itszkaah/ProjetoGrid' },
  { name: 'instagram', language: 'HTML', description: 'Clone ou inspiração de interface do Instagram em HTML e CSS.', url: 'https://github.com/itszkaah/instagram' },
  { name: 'css-grid-menu', language: 'CSS', description: 'Menu de navegação com layout de grid e visual elegante.', url: 'https://github.com/itszkaah/css-grid-menu' },
  { name: 'curriculo', language: 'HTML', description: 'Currículo em formato web com apresentação visual.', url: 'https://github.com/itszkaah/curriculo' },
  { name: 'relogio', language: 'JavaScript', description: 'Projeto de relógio digital/analógico com interação e animação.', url: 'https://github.com/itszkaah/relogio' },
]

const githubRepos = ref([...fallbackRepos, ...extraRepos])
const selectedProject = ref(null)

const scrollToSection = (sectionId) => {
  document.getElementById(sectionId)?.scrollIntoView({ behavior: 'smooth', block: 'start' })
}

const openProject = (project) => {
  selectedProject.value = project
}

const closeProject = () => {
  selectedProject.value = null
}

onMounted(async () => {
  try {
    const response = await fetch('https://api.github.com/users/karinameier01/repos?per_page=20')
    if (!response.ok) throw new Error('GitHub API failed')

    const data = await response.json()
    const known = ['SmartEvent', 'Bookiss', 'AlbumFig', 'FigAlbum', 'meuApp', 'Mini-App', 'joguinho_burro']
    const mapped = data
      .filter((repo) => known.includes(repo.name))
      .slice(0, 6)
      .map((repo) => ({
        name: repo.name,
        language: repo.language || 'Diversos',
        description: repo.description || 'Projeto pessoal em desenvolvimento.',
        url: repo.html_url,
      }))

    if (mapped.length) {
      githubRepos.value = [...mapped, ...extraRepos].slice(0, 12)
    }
  } catch (error) {
    githubRepos.value = [...fallbackRepos, ...extraRepos].slice(0, 12)
  }

  const observer = new IntersectionObserver(
    (entries) => {
      entries.forEach((entry) => {
        if (entry.isIntersecting) {
          entry.target.classList.add('in-view')
        }
      })
    },
    { threshold: 0.18 }
  )

  document.querySelectorAll('.reveal').forEach((element) => observer.observe(element))
})
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700;800&family=Space+Grotesk:wght@500;600;700&family=JetBrains+Mono:wght@400;500;600;700&display=swap');

:global(html) {
  scroll-behavior: smooth;
}

:global(body) {
  margin: 0;
  font-family: 'Inter', sans-serif;
  background: #f2e5c6;
  color: #242124;
}

:global(*) {
  box-sizing: border-box;
}

:global(a) {
  color: inherit;
  text-decoration: none;
}

:global(button) {
  font: inherit;
}

:global(#app) {
  min-height: 100vh;
}

.portfolio-page {
  background: #f2e5c6;
  color: #242124;
}

.site-header {
  position: sticky;
  top: 0;
  z-index: 20;
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 1.2rem;
  padding: 1rem 4vw;
  backdrop-filter: blur(10px);
  background: rgba(242, 229, 198, 0.85);
  border-bottom: 1px solid rgba(117, 22, 45, 0.12);
}

.brand-mark {
  font-family: 'Space Grotesk', sans-serif;
  font-weight: 700;
  letter-spacing: 0.18em;
  font-size: 0.85rem;
  color: #560b18;
}

.main-nav {
  display: flex;
  align-items: center;
  gap: 0.75rem;
  flex-wrap: wrap;
  justify-content: flex-end;
}

.nav-link {
  border: 0;
  background: transparent;
  color: #242124;
  font-size: 0.76rem;
  letter-spacing: 0.12em;
  text-transform: uppercase;
  padding: 0.5rem 0.2rem;
  cursor: pointer;
  position: relative;
}

.nav-link::after {
  content: '';
  position: absolute;
  left: 0;
  bottom: 0;
  width: 100%;
  height: 1px;
  background: #75162d;
  transform: scaleX(0);
  transform-origin: left;
  transition: transform 0.25s ease;
}

.nav-link:hover::after,
.nav-link:focus-visible::after {
  transform: scaleX(1);
}

.page-content {
  width: min(1180px, calc(100% - 32px));
  margin: 0 auto;
  padding-bottom: 3rem;
}

.hero,
.story-section,
.timeline-section,
.feature-split,
.jedi-section,
.projects-section,
.skills-section,
.soft-skills,
.resume-section,
.github-section,
.profile-cta,
.contact-section {
  padding: 5rem 0;
}

.hero {
  display: grid;
  grid-template-columns: 1.15fr 0.85fr;
  gap: 2rem;
  min-height: calc(100vh - 88px);
  align-items: center;
}

.eyebrow {
  margin: 0 0 1.2rem;
  color: #75162d;
  font-size: 0.75rem;
  text-transform: uppercase;
  letter-spacing: 0.18em;
  font-weight: 700;
}

.hero h1,
.story-section h2,
.timeline-section h2,
.feature-split h2,
.jedi-section h2,
.projects-section h2,
.skills-section h2,
.resume-section h2,
.github-section h2,
.contact-section h2,
.profile-cta h2,
.site-footer p {
  font-family: 'Space Grotesk', sans-serif;
  letter-spacing: -0.06em;
  line-height: 0.94;
  margin: 0;
}

.hero h1 {
  font-size: clamp(4rem, 8vw, 9rem);
  line-height: 0.88;
  text-transform: uppercase;
  color: #3b010b;
}

.hero-tagline {
  max-width: 38rem;
  margin: 1.5rem 0 0;
  font-size: clamp(1.1rem, 2vw, 1.5rem);
  line-height: 1.5;
  color: rgba(36, 33, 36, 0.8);
}

.hero-meta {
  display: flex;
  flex-wrap: wrap;
  gap: 1rem 1.5rem;
  margin-top: 2rem;
  color: #560b18;
  font-size: 0.82rem;
  letter-spacing: 0.12em;
  text-transform: uppercase;
}

.cta-row {
  display: flex;
  flex-wrap: wrap;
  gap: 1rem;
  margin-top: 2rem;
}

.button {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  min-height: 48px;
  padding: 0.8rem 1.4rem;
  border-radius: 999px;
  border: 1px solid rgba(117, 22, 45, 0.2);
  cursor: pointer;
  transition: transform 0.2s ease, box-shadow 0.2s ease, filter 0.2s ease;
  font-weight: 600;
  animation: softPulse 6s ease-in-out infinite;
}

.button:hover,
.button:focus-visible {
  transform: translateY(-1px) scale(1.01);
  box-shadow: 0 12px 24px rgba(86, 11, 24, 0.12);
  filter: brightness(1.03);
}

.button.primary {
  background: #75162d;
  color: #fff;
}

.button.secondary {
  background: rgba(255, 255, 255, 0.3);
  color: #3b010b;
}

.hero-visual {
  display: flex;
  justify-content: center;
  align-items: center;
}

.visual-frame {
  position: relative;
  display: flex;
  width: min(520px, 100%);
  min-height: 420px;
  background: linear-gradient(135deg, rgba(117, 22, 45, 0.08), rgba(255, 255, 255, 0.34));
  border: 1px solid rgba(117, 22, 45, 0.12);
  border-radius: 36px;
  padding: 2rem;
  overflow: hidden;
  animation: floatCard 7s ease-in-out infinite;
  box-shadow: 0 28px 48px rgba(86, 11, 24, 0.08);
}

.visual-label {
  position: absolute;
  left: 2rem;
  top: 1.6rem;
  color: #75162d;
  font-size: 0.68rem;
  letter-spacing: 0.2em;
  text-transform: uppercase;
  font-weight: 700;
}

.visual-grid {
  display: grid;
  grid-template-columns: repeat(4, minmax(0, 1fr));
  gap: 0.8rem;
  width: 100%;
  margin-top: 4.2rem;
}

.visual-grid span {
  display: grid;
  place-items: center;
  min-height: 80px;
  border: 1px solid rgba(117, 22, 45, 0.12);
  border-radius: 18px;
  background: rgba(255, 255, 255, 0.32);
  color: #560b18;
  font-family: 'JetBrains Mono', monospace;
  font-size: 0.8rem;
  font-weight: 600;
  animation: hoverLift 5s ease-in-out infinite;
}

.visual-grid span:nth-child(2n) { animation-delay: 0.5s; }
.visual-grid span:nth-child(3n) { animation-delay: 1s; }
.visual-grid span:nth-child(4n) { animation-delay: 1.5s; }

.vertical-line {
  position: absolute;
  right: 2rem;
  top: 1.2rem;
  width: 1px;
  height: calc(100% - 2.4rem);
  background: linear-gradient(180deg, rgba(117, 22, 45, 0.1), rgba(117, 22, 45, 0.6), rgba(117, 22, 45, 0.1));
}

.scroll-cue {
  width: fit-content;
  margin: -0.5rem auto 0;
  padding: 0.7rem 1.2rem;
  border: 1px solid rgba(117, 22, 45, 0.12);
  border-radius: 999px;
  background: rgba(255, 255, 255, 0.18);
  color: #560b18;
  text-transform: uppercase;
  letter-spacing: 0.14em;
  font-size: 0.66rem;
}

.story-section,
.jedi-section,
.resume-section {
  display: grid;
  grid-template-columns: 140px 1fr;
  gap: 2.5rem;
  align-items: start;
}

.section-number {
  font-family: 'Space Grotesk', sans-serif;
  font-size: clamp(2.6rem, 5vw, 5rem);
  color: rgba(117, 22, 45, 0.32);
  line-height: 1;
  margin-top: 0.4rem;
}

.section-copy,
.section-header,
.feature-intro {
  color: #242124;
}

.story-section h2,
.timeline-section h2,
.feature-split h2,
.jedi-section h2,
.projects-section h2,
.skills-section h2,
.resume-section h2,
.github-section h2,
.contact-section h2,
.profile-cta h2 {
  font-size: clamp(2.2rem, 4vw, 4rem);
  margin: 0 0 1.2rem;
}

.section-copy p,
.timeline-content p,
.feature-box p,
.feature-evolution p,
.resume-item p,
.contact-section p,
.repo-card p,
.project-content p,
.modal-copy p,
.skill-block li {
  color: rgba(36, 33, 36, 0.8);
  line-height: 1.7;
  font-size: 1.02rem;
}

.impact-quote {
  padding: 2rem 0 0.5rem;
}

.impact-quote p {
  margin: 0;
  padding: 3rem 2rem;
  text-align: center;
  font-size: clamp(2.2rem, 5vw, 5rem);
  line-height: 1.06;
  font-family: 'Space Grotesk', sans-serif;
  color: #3b010b;
  border-top: 1px solid rgba(117, 22, 45, 0.14);
  border-bottom: 1px solid rgba(117, 22, 45, 0.14);
}

.timeline {
  position: relative;
  display: grid;
  gap: 1.5rem;
  padding-top: 1rem;
}

.timeline::before {
  content: '';
  position: absolute;
  left: 1.8rem;
  top: 0;
  bottom: 0;
  width: 1px;
  background: rgba(117, 22, 45, 0.2);
}

.timeline-item {
  position: relative;
  display: grid;
  grid-template-columns: 120px 1fr;
  gap: 1.5rem;
  padding-left: 2.8rem;
}

.timeline-item::before {
  content: '';
  position: absolute;
  left: 1.35rem;
  top: 0.9rem;
  width: 12px;
  height: 12px;
  border-radius: 50%;
  background: #75162d;
  box-shadow: 0 0 0 6px rgba(117, 22, 45, 0.08);
}

.timeline-year {
  font-family: 'JetBrains Mono', monospace;
  color: #75162d;
  font-size: 0.82rem;
  letter-spacing: 0.12em;
  text-transform: uppercase;
  padding-top: 0.55rem;
}

.timeline-content {
  background: rgba(255, 255, 255, 0.24);
  border: 1px solid rgba(117, 22, 45, 0.08);
  border-radius: 22px;
  padding: 1.2rem 1.4rem;
}

.timeline-content h3,
.skill-block h3,
.repo-topline h3,
.project-content h3,
.modal-header h3,
.contact-card,
.resume-item strong,
.detail-group h4 {
  font-family: 'Space Grotesk', sans-serif;
}

.timeline-content h3 {
  margin: 0 0 0.6rem;
  font-size: clamp(1.4rem, 2vw, 2rem);
  letter-spacing: -0.05em;
}

.feature-split {
  display: grid;
  gap: 2rem;
}

.feature-evolution {
  display: grid;
  grid-template-columns: 1fr auto 1fr;
  gap: 1.2rem;
  align-items: center;
}

.evolution-column,
.feature-box,
.skill-block,
.repo-card,
.contact-card,
.resume-item {
  background: rgba(255, 255, 255, 0.18);
  border: 1px solid rgba(117, 22, 45, 0.12);
  border-radius: 24px;
  padding: 1.3rem 1.2rem;
}

.evolution-column {
  min-height: 178px;
}

.evolution-arrow {
  font-size: 2rem;
  color: #75162d;
}

.small-label,
.resume-label,
.project-topline span {
  display: inline-block;
  margin-bottom: 0.5rem;
  font-size: 0.68rem;
  letter-spacing: 0.14em;
  text-transform: uppercase;
  color: #75162d;
  font-weight: 700;
}

.feature-grid {
  display: grid;
  grid-template-columns: repeat(3, minmax(0, 1fr));
  gap: 1rem;
}

.feature-box.highlight {
  background: rgba(117, 22, 45, 0.08);
}

.projects-section {
  display: grid;
  gap: 2rem;
}

.inline-header {
  display: flex;
  justify-content: space-between;
  align-items: end;
  gap: 1.2rem;
}

.section-copy-mini {
  margin: 0;
  max-width: 24rem;
  color: rgba(36, 33, 36, 0.72);
  line-height: 1.6;
}

.project-layout {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 1.2rem;
}

.project-card {
  display: grid;
  grid-template-columns: 1fr;
  background: rgba(255, 255, 255, 0.2);
  border: 1px solid rgba(117, 22, 45, 0.12);
  border-radius: 28px;
  overflow: hidden;
  cursor: pointer;
  transition: transform 0.25s ease, box-shadow 0.25s ease;
  animation: fadeUp 0.7s ease both;
}

.project-card:hover {
  transform: translateY(-6px) scale(1.01);
  box-shadow: 0 18px 28px rgba(86, 11, 24, 0.08);
}

.project-card.large {
  grid-column: span 2;
}

.project-card.large .project-visual {
  min-height: 300px;
}

.project-visual {
  position: relative;
  min-height: 230px;
  padding: 1.2rem;
  display: flex;
  align-items: flex-start;
  justify-content: space-between;
  border-bottom: 1px solid rgba(117, 22, 45, 0.1);
}

.project-index {
  font-family: 'Space Grotesk', sans-serif;
  font-size: 0.82rem;
  letter-spacing: 0.12em;
  color: rgba(59, 1, 11, 0.8);
  font-weight: 700;
}

.mini-grid {
  display: grid;
  grid-template-columns: repeat(2, minmax(0, 1fr));
  gap: 0.55rem;
  width: 52%;
  max-width: 200px;
  margin-top: 2.2rem;
}

.mini-grid span {
  display: grid;
  place-items: center;
  min-height: 52px;
  border-radius: 12px;
  background: rgba(255, 255, 255, 0.42);
  border: 1px solid rgba(117, 22, 45, 0.08);
  color: #3b010b;
  font-size: 0.68rem;
  letter-spacing: 0.12em;
  text-transform: uppercase;
  font-weight: 700;
}

.project-content {
  padding: 1.2rem 1.2rem 1.4rem;
}

.project-topline {
  display: flex;
  justify-content: space-between;
  gap: 1rem;
  align-items: center;
}

.project-content h3 {
  margin: 0 0 0.6rem;
  font-size: clamp(1.4rem, 2vw, 2.3rem);
  letter-spacing: -0.05em;
}

.chip-row {
  display: flex;
  flex-wrap: wrap;
  gap: 0.6rem;
  margin-top: 1rem;
}

.chip {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  padding: 0.42rem 0.7rem;
  border: 1px solid rgba(117, 22, 45, 0.12);
  border-radius: 999px;
  background: rgba(117, 22, 45, 0.06);
  color: #560b18;
  font-size: 0.68rem;
  letter-spacing: 0.08em;
  text-transform: uppercase;
  font-weight: 700;
}

.skills-grid {
  display: grid;
  grid-template-columns: repeat(3, minmax(0, 1fr));
  gap: 1rem;
}

.skill-block h3 {
  margin: 0 0 1rem;
  font-size: clamp(1.2rem, 1.8vw, 1.8rem);
  letter-spacing: -0.04em;
}

.skill-block ul {
  list-style: none;
  margin: 0;
  padding: 0;
  display: flex;
  flex-wrap: wrap;
  gap: 0.6rem;
}

.skill-block li {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  padding: 0.52rem 0.7rem;
  border-radius: 999px;
  border: 1px solid rgba(117, 22, 45, 0.1);
  background: rgba(117, 22, 45, 0.04);
  color: #3b010b;
  font-size: 0.72rem;
  letter-spacing: 0.06em;
  text-transform: uppercase;
  font-weight: 600;
}

.soft-list {
  display: flex;
  flex-wrap: wrap;
  gap: 0.8rem;
  margin-top: 1.5rem;
}

.soft-list span {
  padding: 0.75rem 1rem;
  background: rgba(255, 255, 255, 0.2);
  border: 1px solid rgba(117, 22, 45, 0.1);
  border-radius: 999px;
  color: #3b010b;
  font-weight: 600;
}

.resume-list {
  display: grid;
  grid-template-columns: repeat(2, minmax(0, 1fr));
  gap: 1rem;
  margin: 1.6rem 0 2rem;
}

.resume-item {
  display: grid;
  gap: 0.4rem;
}

.resume-item strong {
  font-size: clamp(1.1rem, 2vw, 1.8rem);
  letter-spacing: -0.04em;
}

.highlight-item {
  background: rgba(117, 22, 45, 0.06);
}

.github-section {
  display: grid;
  gap: 1.5rem;
}

.repo-grid {
  display: grid;
  grid-template-columns: repeat(3, minmax(0, 1fr));
  gap: 1rem;
}

.repo-card {
  display: grid;
  grid-template-rows: auto auto 1fr auto;
  gap: 0.8rem;
  animation: shimmerCard 7s ease-in-out infinite alternate;
}

.github-links {
  display: flex;
  flex-wrap: wrap;
  gap: 0.75rem;
}

.repo-topline {
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 1rem;
}

.repo-topline h3 {
  margin: 0;
  font-size: clamp(1.2rem, 2vw, 1.8rem);
  letter-spacing: -0.03em;
}

.repo-card a {
  color: #75162d;
  font-weight: 700;
}

.profile-cta {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 2rem;
  padding: 2rem 2.2rem;
  background: rgba(117, 22, 45, 0.06);
  border: 1px solid rgba(117, 22, 45, 0.12);
  border-radius: 28px;
}

.contact-section {
  display: grid;
  gap: 1.2rem;
  padding-bottom: 3rem;
}

.contact-grid {
  display: grid;
  grid-template-columns: repeat(4, minmax(0, 1fr));
  gap: 1rem;
  margin-top: 0.75rem;
}

.contact-card {
  display: inline-flex;
  justify-content: center;
  align-items: center;
  min-height: 82px;
  text-align: center;
  color: #3b010b;
  font-weight: 600;
  font-size: 1.02rem;
}

.site-footer {
  border-top: 1px solid rgba(117, 22, 45, 0.12);
  padding: 2.4rem 4vw 4rem;
  text-align: center;
  background: rgba(255, 255, 255, 0.08);
}

.site-footer p {
  font-size: clamp(2.2rem, 4vw, 4.2rem);
  color: #3b010b;
  margin-bottom: 1rem;
}

.footer-meta {
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
  gap: 0.8rem 1.2rem;
  color: #560b18;
  letter-spacing: 0.12em;
  text-transform: uppercase;
  font-size: 0.7rem;
}

.site-footer small {
  display: block;
  margin-top: 1rem;
  color: rgba(36, 33, 36, 0.7);
}

.project-modal {
  position: fixed;
  inset: 0;
  background: rgba(36, 33, 36, 0.42);
  display: grid;
  place-items: center;
  padding: 1rem;
  z-index: 30;
}

.modal-panel {
  width: min(920px, 100%);
  background: #f7efe4;
  border: 1px solid rgba(117, 22, 45, 0.14);
  border-radius: 30px;
  box-shadow: 0 32px 60px rgba(36, 33, 36, 0.2);
  padding: 1.5rem;
}

.modal-close {
  display: inline-flex;
  margin-left: auto;
  border: 1px solid rgba(117, 22, 45, 0.15);
  background: rgba(117, 22, 45, 0.04);
  color: #560b18;
  border-radius: 999px;
  padding: 0.5rem 0.9rem;
  cursor: pointer;
  margin-bottom: 1rem;
}

.modal-header h3 {
  margin: 0;
  font-size: clamp(2.2rem, 4vw, 3rem);
  letter-spacing: -0.06em;
}

.modal-body {
  display: grid;
  grid-template-columns: 0.95fr 1.05fr;
  gap: 1.2rem;
  align-items: start;
}

.modal-visual {
  min-height: 320px;
  border-radius: 24px;
  border: 1px solid rgba(117, 22, 45, 0.12);
  padding: 1rem;
  display: flex;
  align-items: flex-start;
  justify-content: flex-end;
}

.wide-grid {
  width: 100%;
  max-width: 100%;
  margin-top: 1.5rem;
}

.modal-copy {
  display: grid;
  gap: 1rem;
}

.detail-group h4 {
  margin: 0 0 0.4rem;
  font-size: 1.1rem;
  color: #3b010b;
}

.reveal {
  opacity: 0;
  transform: translateY(28px);
  transition: opacity 0.7s ease, transform 0.7s ease;
}

.reveal.in-view {
  opacity: 1;
  transform: translateY(0);
}

@keyframes floatCard {
  0%, 100% { transform: translateY(0); }
  50% { transform: translateY(-12px); }
}

@keyframes hoverLift {
  0%, 100% { transform: translateY(0); }
  50% { transform: translateY(-6px); }
}

@keyframes softPulse {
  0%, 100% { box-shadow: 0 0 0 rgba(117, 22, 45, 0.0); }
  50% { box-shadow: 0 0 24px rgba(117, 22, 45, 0.12); }
}

@keyframes fadeUp {
  from { opacity: 0; transform: translateY(16px); }
  to { opacity: 1; transform: translateY(0); }
}

@keyframes shimmerCard {
  0% { box-shadow: 0 0 0 rgba(117, 22, 45, 0.0); }
  100% { box-shadow: 0 20px 40px rgba(117, 22, 45, 0.08); }
}

@media (max-width: 900px) {
  .hero,
  .story-section,
  .jedi-section,
  .resume-section,
  .modal-body,
  .profile-cta,
  .feature-evolution {
    grid-template-columns: 1fr;
  }

  .project-layout,
  .repo-grid,
  .skills-grid,
  .contact-grid,
  .feature-grid,
  .resume-list {
    grid-template-columns: 1fr 1fr;
  }

  .project-card.large {
    grid-column: auto;
  }

  .profile-cta {
    display: grid;
    justify-content: stretch;
    text-align: left;
  }
}

@media (max-width: 680px) {
  .site-header {
    flex-direction: column;
    align-items: flex-start;
    padding-top: 0.8rem;
  }

  .main-nav {
    justify-content: flex-start;
    gap: 0.5rem 1rem;
  }

  .hero {
    min-height: auto;
    padding-top: 3rem;
  }

  .project-layout,
  .repo-grid,
  .skills-grid,
  .contact-grid,
  .feature-grid,
  .resume-list,
  .timeline-item {
    grid-template-columns: 1fr;
  }

  .timeline::before {
    left: 0.7rem;
  }

  .timeline-item {
    padding-left: 1.5rem;
  }

  .timeline-item::before {
    left: 0.25rem;
  }

  .timeline-year {
    padding-top: 0;
  }

  .project-card.large {
    grid-column: span 1;
  }

  .modal-panel {
    padding: 1rem;
  }

  .button,
  .nav-link {
    letter-spacing: 0.08em;
  }
}

@media (prefers-reduced-motion: reduce) {
  :global(html) {
    scroll-behavior: auto;
  }

  .reveal,
  .button,
  .nav-link,
  .project-card {
    transition: none !important;
    transform: none !important;
    opacity: 1 !important;
  }
}
</style>
