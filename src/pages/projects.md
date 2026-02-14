---
layout: ../layouts/ProjectsLayout.astro
title: "Projects"
projects:
  - title: "Group Policy Object manager for Windows - Smart India Hackathon 2024"
    description: "A Windows application developed to generate and manage customized Group Policy Objects (GPOs) aligned with CIS security benchmarks. Selected as a Finalist at Smart India Hackathon 2024."
    techStack: [".NET", "C#", "WPF"]
    githubLink: "https://github.com/AJ0070/Techolics_"
    imageSrc: "/assets/projects/SIH.jpg"

  - title: "CurveFit.jl — StatsAPI Integration"
    description: "Integrated StatsAPI to expose critical statistical metrics (Variance-Covariance Matrix, Standard Error) for nonlinear least squares solutions, bringing feature parity with major scientific libraries."
    techStack: ["Julia", "Mathematics", "Statistics"]
    githubLink: "https://github.com/SciML/CurveFit.jl/pull/63"

  - title: "Symbolics.jl — SymPy Translation Layer"
    description: "Implemented an automatic translation layer to bridge Symbolics.jl with SymPy, creating wrapper functions that allow users to leverage SymPy's powerful solvers (integrals, limits) directly within Julia. Awarded $300 Bounty."
    techStack: ["Julia", "SymPy", "Mathematics"]
    githubLink: "https://github.com/JuliaSymbolics/Symbolics.jl/pull/1560"

  - title: "NonlinearSolve.jl — AD Refactoring"
    description: "Refactored automatic differentiation (AD) wrappers to improve compatibility with DifferentiationInterface, optimizing solver performance for complex numerical tasks."
    techStack: ["Julia", "Automatic Differentiation"]
    githubLink: "https://github.com/SciML/NonlinearSolve.jl/pull/699"

  - title: "Flexile — Payment Notification System"
    description: "Engineered a failure notification system that captures WiseError exceptions during payment processing and triggers automated, detailed email alerts to contractors, significantly improving transparency. Awarded $2,500 Bounty."
    techStack: ["Ruby on Rails", "PostgreSQL"]
    githubLink: "https://github.com/antiwork/flexile/pull/773"

  - title: "Flexile — Payment Reconciliation"
    description: "Implemented logic to handle Wise payment refunds and dividend cancellations, ensuring the system correctly updates payment statuses from 'processing' to 'failed' when external cancellations occur. Awarded $2,500 Bounty."
    techStack: ["Ruby on Rails", "PostgreSQL"]
    githubLink: "https://github.com/antiwork/flexile/pull/430"

  - title: "Coder Registry — PGAdmin Module"
    description: "Developed and merged the PGAdmin module into the Coder Registry, allowing developers to deploy PostgreSQL administration interfaces instantly within their cloud workspaces. Awarded $50 Bounty."
    techStack: ["Terraform", "HCL"]
    githubLink: "https://github.com/coder/registry/pull/228"

  - title: "Portfolio Website"
    description: "My personal portfolio and blog — built with Astro and deployed for showcasing projects, skills, and achievements."
    techStack: ["Astro", "ReactJS", "Pagefind", "TailwindCSS"]
    githubLink: "https://github.com/AJ0070"
---
