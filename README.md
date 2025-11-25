
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Status de Termos e Categorias</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        :root {
            --primary-color: #2c3e50;
            --secondary-color: #3498db;
            --pilot-color: #f39c12;
            --pending-color: #e74c3c;
            --light-gray: #f5f5f5;
            --border-color: #ddd;
            --distrato-color: #3498db;
            --quitacao-color: #2ecc71;
            --cessao-color: #9b59b6;
            --renegociacao-color: #e67e22;
            --igma-color: #2196f3;
        }
        
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background-color: #f9f9f9;
            color: #333;
            line-height: 1.6;
            padding: 20px;
            background: linear-gradient(135deg, #f5f7fa 0%, #c3cfe2 100%);
            min-height: 100vh;
        }
        
        .container {
            max-width: 1400px;
            margin: 0 auto;
            background-color: white;
            border-radius: 12px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
            padding: 25px;
            position: relative;
            overflow: hidden;
        }
        
        .container::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 5px;
            background: linear-gradient(90deg, var(--distrato-color), var(--quitacao-color), var(--cessao-color), var(--renegociacao-color));
        }
        
        header {
            text-align: center;
            margin-bottom: 30px;
            padding-bottom: 20px;
            border-bottom: 1px solid var(--border-color);
            position: relative;
        }
        
        h1 {
            color: var(--primary-color);
            margin-bottom: 10px;
            font-size: 2.2rem;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 15px;

        }
        
        .filters {
            display: flex;
            flex-wrap: wrap;
            gap: 15px;
            margin-bottom: 25px;
            padding: 20px;
            background-color: var(--light-gray);
            border-radius: 8px;
            box-shadow: 0 2px 5px rgba(0,0,0,0.05);
        }
        
        .filter-group {
            flex: 1;
            min-width: 200px;
        }
        
        label {
            display: block;
            margin-bottom: 8px;
            font-weight: 600;
            color: var(--primary-color);
        }
        
        select, input {
            width: 100%;
            padding: 10px 15px;
            border: 1px solid var(--border-color);
            border-radius: 6px;
            font-size: 15px;
            transition: all 0.3s;
        }
        
        select:focus, input:focus {
            outline: none;
            border-color: var(--secondary-color);
            box-shadow: 0 0 0 3px rgba(52, 152, 219, 0.2);
        }
        
        .table-container {
            overflow-x: auto;
            border-radius: 8px;
            border: 1px solid var(--border-color);
            margin-bottom: 30px;
            box-shadow: 0 2px 5px rgba(0,0,0,0.05);
        }
        
        table {
            width: 100%;
            border-collapse: collapse;
        }
        
        th, td {
            padding: 14px 18px;
            text-align: left;
            border-bottom: 1px solid var(--border-color);
        }
        
        thead {
            background-color: var(--primary-color);
            color: white;
        }
        
        thead th {
            font-weight: 600;
            position: relative;
        }
        
        thead th:after {
            content: '';
            position: absolute;
            bottom: 0;
            left: 0;
            width: 100%;
            height: 3px;
            background: rgba(255,255,255,0.3);
        }
        
        tbody tr {
            transition: all 0.2s;
        }
        
        tbody tr:hover {
            background-color: rgba(52, 152, 219, 0.05);
            cursor: pointer;
            transform: translateY(-2px);
            box-shadow: 0 3px 8px rgba(0,0,0,0.1);
        }
        
        .status {
            display: inline-block;
            padding: 6px 12px;
            border-radius: 20px;
            font-size: 12px;
            font-weight: 600;
        }
        
        .status-pilotagem {
            background-color: var(--pilot-color);
            color: white;
        }
        
        .status-pendente {
            background-color: var(--pending-color);
            color: white;
        }
        
        .category-distrato {
            border-left: 4px solid var(--distrato-color);
        }
        
        .category-quitacao {
            border-left: 4px solid var(--quitacao-color);
        }
        
        .category-cessao {
            border-left: 4px solid var(--cessao-color);
        }
        
        .category-renegociacao {
            border-left: 4px solid var(--renegociacao-color);
        }
        
        .summary {
            display: flex;
            flex-wrap: wrap;
            gap: 20px;
            margin-bottom: 30px;
        }
        
        .summary-card {
            flex: 1;
            min-width: 200px;
            padding: 20px;
            border-radius: 8px;
            background-color: white;
            text-align: center;
            box-shadow: 0 3px 10px rgba(0,0,0,0.08);
            transition: transform 0.3s;
        }
        
        .summary-card:hover {
            transform: translateY(-5px);
        }
        
        .summary-card h3 {
            font-size: 14px;
            margin-bottom: 10px;
            color: var(--primary-color);
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 8px;
        }
        
        .summary-card p {
            font-size: 28px;
            font-weight: bold;
            color: var(--primary-color);
        }
        
        .summary-card.total {
            border-top: 4px solid var(--primary-color);
        }
        
        .summary-card.pilot {
            border-top: 4px solid var(--pilot-color);
        }
        
        .summary-card.pending {
            border-top: 4px solid var(--pending-color);
        }
        
        .summary-card.adjustments {
            border-top: 4px solid var(--igma-color);
        }
        
        .adjustments-section {
            margin-top: 30px;
        }
        
        .adjustments-section h2 {
            color: var(--primary-color);
            margin-bottom: 20px;
            padding-bottom: 10px;
            border-bottom: 1px solid var(--border-color);
            display: flex;
            align-items: center;
            gap: 10px;
        }
        
        .adjustment-item {
            background-color: white;
            border-radius: 8px;
            padding: 20px;
            margin-bottom: 20px;
            border-left: 4px solid var(--pending-color);
            box-shadow: 0 3px 10px rgba(0,0,0,0.08);
            transition: transform 0.2s;
        }
        
        .adjustment-item:hover {
            transform: translateX(5px);
        }
        
        .adjustment-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 15px;
        }
        
        .adjustment-title {
            font-weight: 600;
            color: var(--primary-color);
            font-size: 1.1rem;
        }
        
        .adjustment-category {
            display: inline-block;
            padding: 5px 12px;
            border-radius: 20px;
            font-size: 12px;
            font-weight: 600;
            color: white;
        }
        
        .category-distrato-badge {
            background-color: var(--distrato-color);
        }
        
        .category-quitacao-badge {
            background-color: var(--quitacao-color);
        }
        
        .category-cessao-badge {
            background-color: var(--cessao-color);
        }
        
        .category-renegociacao-badge {
            background-color: var(--renegociacao-color);
        }
        
        .adjustment-details {
            margin-top: 15px;
        }
        
        .adjustment-tags {
            display: flex;
            flex-wrap: wrap;
            gap: 8px;
            margin-top: 12px;
        }
        
        .tag {
            background-color: #e0e0e0;
            padding: 5px 12px;
            border-radius: 15px;
            font-size: 12px;
            font-weight: 500;
        }
        
        .priority-high {
            background-color: #ffebee;
            border-left-color: #e53935;
        }
        
        .priority-medium {
            background-color: #fff8e1;
            border-left-color: #ffb300;
        }
        
        .priority-low {
            background-color: #e8f5e8;
            border-left-color: #43a047;
        }
        
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.5);
            z-index: 1000;
            justify-content: center;
            align-items: center;
            backdrop-filter: blur(3px);
        }
        
        .modal-content {
            background-color: white;
            padding: 25px;
            border-radius: 12px;
            width: 90%;
            max-width: 800px;
            max-height: 90vh;
            overflow-y: auto;
            box-shadow: 0 10px 30px rgba(0,0,0,0.2);
            position: relative;
        }
        
        .modal-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 20px;
            padding-bottom: 15px;
            border-bottom: 1px solid var(--border-color);
        }
        
        .close-modal {
            background: none;
            border: none;
            font-size: 28px;
            cursor: pointer;
            color: #666;
            transition: color 0.3s;
        }
        
        .close-modal:hover {
            color: var(--pending-color);
        }
        
        .modal-body {
            margin-bottom: 20px;
        }
        
        .modal-footer {
            text-align: right;
        }
        
        .btn {
            padding: 10px 20px;
            border: none;
            border-radius: 6px;
            cursor: pointer;
            font-weight: 600;
            transition: all 0.3s;
        }
        
        .btn-primary {
            background-color: var(--secondary-color);
            color: white;
        }
        
        .btn-primary:hover {
            background-color: #2980b9;
            transform: translateY(-2px);
            box-shadow: 0 4px 8px rgba(0,0,0,0.1);
        }
        
        .igma-highlight {
            background-color: #e3f2fd;
            border-left: 4px solid var(--igma-color);
        }
        
        .igma-tag {
            background-color: var(--igma-color);
            color: white;
        }
        
        .no-adjustments {
            text-align: center;
            padding: 30px;
            color: #666;
            font-style: italic;
        }
        
        .footer {
            margin-top: 40px;
            text-align: center;
            color: #666;
            font-size: 0.9rem;
            padding-top: 20px;
            border-top: 1px solid var(--border-color);
        }
        
        @media (max-width: 768px) {
            .filters {
                flex-direction: column;
            }
            
            .filter-group {
                width: 100%;
            }
            
            th, td {
                padding: 10px 12px;
            }
            
            .adjustment-header {
                flex-direction: column;
                align-items: flex-start;
                gap: 10px;
            }
            
            h1 {
                font-size: 1.8rem;
            }
        }
        
        .export-btn {
            display: inline-flex;
            align-items: center;
            gap: 8px;
            background-color: var(--quitacao-color);
            color: white;
            border: none;
            padding: 10px 20px;
            border-radius: 6px;
            cursor: pointer;
            font-weight: 600;
            transition: all 0.3s;
            margin-top: 10px;
        }
        
        .export-btn:hover {
            background-color: #27ae60;
            transform: translateY(-2px);
            box-shadow: 0 4px 8px rgba(0,0,0,0.1);
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <h1><i class="fas fa-file-contract"></i> Status de Termos e Categorias</h1>
            <p class="description">Visualize e filtre os termos por categoria e status, incluindo detalhes sobre ajustes pendentes. A tabela interativa permite uma análise detalhada do andamento de cada documento.</p>
        </header>
        
        <div class="filters">
            <div class="filter-group">
                <label for="categoryFilter"><i class="fas fa-filter"></i> Filtrar por Categoria:</label>
                <select id="categoryFilter">
                    <option value="">Todas as categorias</option>
                    <option value="DISTRATO">DISTRATO</option>
                    <option value="TERMO DE QUITAÇÃO">TERMO DE QUITAÇÃO</option>
                    <option value="CESSÃO DE DIREITOS">CESSÃO DE DIREITOS</option>
                    <option value="RENEGOCIAÇÃO">RENEGOCIAÇÃO</option>
                </select>
            </div>
            
            <div class="filter-group">
                <label for="statusFilter"><i class="fas fa-tasks"></i> Filtrar por Status:</label>
                <select id="statusFilter">
                    <option value="">Todos os status</option>
                    <option value="EM PILOTAGEM">EM PILOTAGEM</option>
                    <option value="PENDENTE">PENDENTE</option>
                </select>
            </div>
            
            <div class="filter-group">
                <label for="searchTerm"><i class="fas fa-search"></i> Buscar por Termo:</label>
                <input type="text" id="searchTerm" placeholder="Digite um termo...">
            </div>
        </div>
        
        <div class="summary">
            <div class="summary-card total">
                <h3><i class="fas fa-file-alt"></i> Total de Termos</h3>
                <p id="totalTerms">0</p>
            </div>
            <div class="summary-card pilot">
                <h3><i class="fas fa-rocket"></i> Em Pilotagem</h3>
                <p id="pilotTerms">0</p>
            </div>
            <div class="summary-card pending">
                <h3><i class="fas fa-clock"></i> Pendentes</h3>
                <p id="pendingTerms">0</p>
            </div>
            <div class="summary-card adjustments">
                <h3><i class="fas fa-tools"></i> Ajustes Pendentes</h3>
                <p id="pendingAdjustments">0</p>
            </div>
        </div>
        
        <div class="table-container">
            <table id="termsTable">
                <thead>
                    <tr>
                        <th>CATEGORIA</th>
                        <th>TERMO</th>
                        <th>STATUS</th>
                        <th>DETALHES</th>
                    </tr>
                </thead>
                <tbody>
                    <!-- Os dados serão preenchidos via JavaScript -->
                </tbody>
            </table>
        </div>
        
        <button class="export-btn" id="exportBtn">
            <i class="fas fa-download"></i> Exportar Relatório
        </button>
        
        <div class="adjustments-section">
            <h2><i class="fas fa-clipboard-list"></i> Detalhes dos Ajustes Pendentes</h2>
            <div id="adjustmentsList">
                <!-- Os ajustes serão preenchidos via JavaScript -->
            </div>
        </div>
        
        <div class="footer">
            <p>Sistema de Gestão de Termos - Desenvolvido para acompanhamento de status e ajustes</p>
        </div>
    </div>

    <!-- Modal para detalhes do termo -->
    <div id="termModal" class="modal">
        <div class="modal-content">
            <div class="modal-header">
                <h2 id="modalTitle">Detalhes do Termo</h2>
                <button class="close-modal">&times;</button>
            </div>
            <div class="modal-body" id="modalBody">
                <!-- Conteúdo será preenchido via JavaScript -->
            </div>
            <div class="modal-footer">
                <button class="btn btn-primary" id="closeModalBtn">Fechar</button>
            </div>
        </div>
    </div>

    <script>
        // Dados da tabela
        const tableData = [
            { 
                categoria: "DISTRATO", 
                termo: "DISTRATO COM ESTORNO", 
                status: "EM PILOTAGEM",
                ajustes: [
                    {
                        tipo: "Ajuste Técnico - IGMA",
                        descricao: "Integração com sistema IGMA para processamento de estornos",
                        prioridade: "alta",
                        tags: ["IGMA", "estorno", "integração", "financeiro"]
                    }
                ]
            },
            { 
                categoria: "DISTRATO", 
                termo: "DISTRATO COM ESTORNO E REEMBOLSO", 
                status: "EM PILOTAGEM",
                ajustes: [
                    {
                        tipo: "Ajuste Técnico - IGMA",
                        descricao: "Integração com sistema IGMA para processamento de estornos e reembolsos",
                        prioridade: "alta",
                        tags: ["IGMA", "estorno", "reembolso", "integração", "financeiro"]
                    }
                ]
            },
            { 
                categoria: "DISTRATO", 
                termo: "DISTRATO COM REEMBOLSO", 
                status: "EM PILOTAGEM",
                ajustes: [
                    {
                        tipo: "Ajuste Técnico - IGMA",
                        descricao: "Integração com sistema IGMA para processamento de reembolsos",
                        prioridade: "alta",
                        tags: ["IGMA", "reembolso", "integração", "financeiro"]
                    }
                ]
            },
            { 
                categoria: "DISTRATO", 
                termo: "DISTRATO COM RETENÇÃO", 
                status: "EM PILOTAGEM",
                ajustes: [
                    {
                        tipo: "Ajuste Técnico - IGMA",
                        descricao: "Integração com sistema IGMA para processamento de retenções",
                        prioridade: "alta",
                        tags: ["IGMA", "retenção", "integração", "financeiro"]
                    }
                ]
            },
            { 
                categoria: "DISTRATO", 
                termo: "DISTRATO COM RETENÇÃO E REEMBOLSO", 
                status: "EM PILOTAGEM",
                ajustes: [
                    {
                        tipo: "Ajuste Técnico - IGMA",
                        descricao: "Integração com sistema IGMA para processamento de retenções e reembolsos",
                        prioridade: "alta",
                        tags: ["IGMA", "retenção", "reembolso", "integração", "financeiro"]
                    }
                ]
            },
            { 
                categoria: "DISTRATO", 
                termo: "DISTRATO COM REAPROVEITAMENTO", 
                status: "PENDENTE",
                ajustes: [
                    {
                        tipo: "Ajustes Técnicos",
                        descricao: "Revisão e adequação dos parâmetros técnicos do documento",
                        prioridade: "alta",
                        tags: ["backend", "integração", "validações"]
                    },
                    {
                        tipo: "Formatação de Expressões",
                        descricao: "Ajuste na formatação de expressões matemáticas e jurídicas",
                        prioridade: "média",
                        tags: ["layout", "visual", "expressões"]
                    },
                    {
                        tipo: "Campos de Assinatura",
                        descricao: "Adequação dos campos de assinatura digital e física",
                        prioridade: "alta",
                        tags: ["assinatura", "certificação", "validação"]
                    },
                    {
                        tipo: "Ajuste Técnico - IGMA",
                        descricao: "Integração com sistema IGMA para reaproveitamento de contratos",
                        prioridade: "alta",
                        tags: ["IGMA", "reaproveitamento", "integração", "contratos"]
                    }
                ]
            },
            { 
                categoria: "TERMO DE QUITAÇÃO", 
                termo: "TERMO DE QUITAÇÃO", 
                status: "PENDENTE",
                ajustes: [
                    {
                        tipo: "Estágio do Documento",
                        descricao: "Definição dos estágios de tramitação do documento",
                        prioridade: "alta",
                        tags: ["workflow", "estágios", "aprovação"]
                    },
                    {
                        tipo: "Nomenclatura",
                        descricao: "Padronização da nomenclatura utilizada no documento",
                        prioridade: "média",
                        tags: ["padronização", "terminologia"]
                    },
                    {
                        tipo: "Tags",
                        descricao: "Inserção de tags para categorização e busca",
                        prioridade: "baixa",
                        tags: ["metadados", "categorização"]
                    },
                    {
                        tipo: "Mapeamento de Carta de Crédito",
                        descricao: "Integração com sistema de cartas de crédito",
                        prioridade: "alta",
                        tags: ["integração", "financeiro", "crédito"]
                    }
                ]
            },
            { 
                categoria: "CESSÃO DE DIREITOS", 
                termo: "CESSÃO DE DIREITOS", 
                status: "PENDENTE",
                ajustes: [
                    {
                        tipo: "Ajustes Técnicos",
                        descricao: "Revisão dos aspectos técnicos da cessão de direitos",
                        prioridade: "alta",
                        tags: ["jurídico", "validação"]
                    },
                    {
                        tipo: "Formatação de Expressões",
                        descricao: "Ajuste na formatação de cláusulas e expressões jurídicas",
                        prioridade: "média",
                        tags: ["layout", "cláusulas"]
                    },
                    {
                        tipo: "Campos de Assinatura",
                        descricao: "Adequação dos campos para assinatura das partes",
                        prioridade: "alta",
                        tags: ["assinatura", "partes"]
                    },
                    {
                        tipo: "Nomenclatura",
                        descricao: "Padronização dos termos jurídicos utilizados",
                        prioridade: "média",
                        tags: ["jurídico", "terminologia"]
                    }
                ]
            },
            { 
                categoria: "RENEGOCIAÇÃO", 
                termo: "ADITIVO DE RENEGOCIAÇÃO", 
                status: "PENDENTE",
                ajustes: [
                    {
                        tipo: "Estágio do Documento",
                        descricao: "Definição do fluxo de aprovação da renegociação",
                        prioridade: "alta",
                        tags: ["workflow", "aprovação"]
                    },
                    {
                        tipo: "Nomenclatura",
                        descricao: "Padronização dos termos financeiros e contratuais",
                        prioridade: "média",
                        tags: ["financeiro", "contratual"]
                    },
                    {
                        tipo: "Tags",
                        descricao: "Inserção de tags para controle e monitoramento",
                        prioridade: "baixa",
                        tags: ["metadados", "controle"]
                    },
                    {
                        tipo: "Mapeamento de Carta de Crédito",
                        descricao: "Integração com sistema de crédito para renegociação",
                        prioridade: "alta",
                        tags: ["integração", "crédito", "financeiro"]
                    }
                ]
            }
        ];

        // Elementos DOM
        const tableBody = document.querySelector('#termsTable tbody');
        const categoryFilter = document.getElementById('categoryFilter');
        const statusFilter = document.getElementById('statusFilter');
        const searchTerm = document.getElementById('searchTerm');
        const totalTerms = document.getElementById('totalTerms');
        const pilotTerms = document.getElementById('pilotTerms');
        const pendingTerms = document.getElementById('pendingTerms');
        const pendingAdjustments = document.getElementById('pendingAdjustments');
        const adjustmentsList = document.getElementById('adjustmentsList');
        const termModal = document.getElementById('termModal');
        const modalTitle = document.getElementById('modalTitle');
        const modalBody = document.getElementById('modalBody');
        const closeModalBtn = document.getElementById('closeModalBtn');
        const closeModalX = document.querySelector('.close-modal');
        const exportBtn = document.getElementById('exportBtn');

        // Função para renderizar a tabela
        function renderTable(data) {
            tableBody.innerHTML = '';
            
            data.forEach(item => {
                const row = document.createElement('tr');
                
                // Adiciona classe baseada na categoria para estilização
                if (item.categoria === "DISTRATO") row.classList.add('category-distrato');
                else if (item.categoria === "TERMO DE QUITAÇÃO") row.classList.add('category-quitacao');
                else if (item.categoria === "CESSÃO DE DIREITOS") row.classList.add('category-cessao');
                else if (item.categoria === "RENEGOCIAÇÃO") row.classList.add('category-renegociacao');
                
                // Adiciona evento de clique para abrir modal com detalhes
                row.addEventListener('click', () => openTermModal(item));
                
                row.innerHTML = `
                    <td>${item.categoria}</td>
                    <td>${item.termo}</td>
                    <td><span class="status ${item.status === 'EM PILOTAGEM' ? 'status-pilotagem' : 'status-pendente'}">${item.status}</span></td>
                    <td>${item.ajustes.length > 0 ? `<i class="fas fa-exclamation-triangle" style="color: #e74c3c;"></i> ${item.ajustes.length} ajuste(s) pendente(s)` : '<i class="fas fa-check-circle" style="color: #2ecc71;"></i> Sem ajustes pendentes'}</td>
                `;
                
                tableBody.appendChild(row);
            });
            
            updateSummary(data);
            renderAdjustments(data);
        }

        // Função para atualizar o resumo
        function updateSummary(data) {
            totalTerms.textContent = data.length;
            pilotTerms.textContent = data.filter(item => item.status === 'EM PILOTAGEM').length;
            pendingTerms.textContent = data.filter(item => item.status === 'PENDENTE').length;
            
            // Calcular total de ajustes pendentes
            const totalAdjustments = data.reduce((total, item) => total + item.ajustes.length, 0);
            pendingAdjustments.textContent = totalAdjustments;
        }

        // Função para renderizar a lista de ajustes
        function renderAdjustments(data) {
            adjustmentsList.innerHTML = '';
            
            // Filtrar apenas itens com ajustes pendentes
            const itemsWithAdjustments = data.filter(item => item.ajustes.length > 0);
            
            if (itemsWithAdjustments.length === 0) {
                adjustmentsList.innerHTML = '<div class="no-adjustments"><i class="fas fa-check-circle" style="font-size: 2rem; margin-bottom: 10px; color: #2ecc71;"></i><p>Não há ajustes pendentes para os filtros aplicados.</p></div>';
                return;
            }
            
            itemsWithAdjustments.forEach(item => {
                const adjustmentContainer = document.createElement('div');
                adjustmentContainer.classList.add('adjustment-item');
                
                // Adiciona classe de prioridade baseada no primeiro ajuste (para simplificar)
                if (item.ajustes.some(ajuste => ajuste.prioridade === 'alta')) {
                    adjustmentContainer.classList.add('priority-high');
                } else if (item.ajustes.some(ajuste => ajuste.prioridade === 'média')) {
                    adjustmentContainer.classList.add('priority-medium');
                } else {
                    adjustmentContainer.classList.add('priority-low');
                }
                
                // Destacar ajustes com IGMA
                if (item.ajustes.some(ajuste => ajuste.tipo.includes('IGMA'))) {
                    adjustmentContainer.classList.add('igma-highlight');
                }
                
                let categoryBadgeClass = '';
                if (item.categoria === "DISTRATO") categoryBadgeClass = 'category-distrato-badge';
                else if (item.categoria === "TERMO DE QUITAÇÃO") categoryBadgeClass = 'category-quitacao-badge';
                else if (item.categoria === "CESSÃO DE DIREITOS") categoryBadgeClass = 'category-cessao-badge';
                else if (item.categoria === "RENEGOCIAÇÃO") categoryBadgeClass = 'category-renegociacao-badge';
                
                let adjustmentsHTML = '';
                item.ajustes.forEach(ajuste => {
                    let priorityIcon = '';
                    if (ajuste.prioridade === 'alta') {
                        priorityIcon = '<i class="fas fa-exclamation-circle" style="color: #e53935;"></i>';
                    } else if (ajuste.prioridade === 'média') {
                        priorityIcon = '<i class="fas fa-exclamation-triangle" style="color: #ffb300;"></i>';
                    } else {
                        priorityIcon = '<i class="fas fa-info-circle" style="color: #43a047;"></i>';
                    }
                    
                    let tagsHTML = '';
                    if (ajuste.tags && ajuste.tags.length > 0) {
                        tagsHTML = `<div class="adjustment-tags">${ajuste.tags.map(tag => {
                            if (tag === 'IGMA') {
                                return `<span class="tag igma-tag"><i class="fas fa-cog"></i> ${tag}</span>`;
                            } else {
                                return `<span class="tag">${tag}</span>`;
                            }
                        }).join('')}</div>`;
                    }
                    
                    adjustmentsHTML += `
                        <div class="adjustment-details">
                            <h4>${priorityIcon} ${ajuste.tipo}</h4>
                            <p>${ajuste.descricao}</p>
                            ${tagsHTML}
                        </div>
                    `;
                });
                
                adjustmentContainer.innerHTML = `
                    <div class="adjustment-header">
                        <div class="adjustment-title">${item.termo}</div>
                        <span class="adjustment-category ${categoryBadgeClass}">${item.categoria}</span>
                    </div>
                    ${adjustmentsHTML}
                `;
                
                adjustmentsList.appendChild(adjustmentContainer);
            });
        }

        // Função para filtrar os dados
        function filterData() {
            const categoryValue = categoryFilter.value;
            const statusValue = statusFilter.value;
            const searchValue = searchTerm.value.toLowerCase();
            
            const filteredData = tableData.filter(item => {
                const categoryMatch = categoryValue === '' || item.categoria === categoryValue;
                const statusMatch = statusValue === '' || item.status === statusValue;
                const searchMatch = item.termo.toLowerCase().includes(searchValue) || 
                                   item.categoria.toLowerCase().includes(searchValue);
                
                return categoryMatch && statusMatch && searchMatch;
            });
            
            renderTable(filteredData);
        }

        // Função para abrir modal com detalhes do termo
        function openTermModal(item) {
            modalTitle.textContent = item.termo;
            
            let categoryBadgeClass = '';
            if (item.categoria === "DISTRATO") categoryBadgeClass = 'category-distrato-badge';
            else if (item.categoria === "TERMO DE QUITAÇÃO") categoryBadgeClass = 'category-quitacao-badge';
            else if (item.categoria === "CESSÃO DE DIREITOS") categoryBadgeClass = 'category-cessao-badge';
            else if (item.categoria === "RENEGOCIAÇÃO") categoryBadgeClass = 'category-renegociacao-badge';
            
            let statusClass = item.status === 'EM PILOTAGEM' ? 'status-pilotagem' : 'status-pendente';
            
            let adjustmentsHTML = '';
            if (item.ajustes.length > 0) {
                item.ajustes.forEach(ajuste => {
                    let priorityIcon = '';
                    if (ajuste.prioridade === 'alta') {
                        priorityIcon = '<i class="fas fa-exclamation-circle" style="color: #e53935;"></i>';
                    } else if (ajuste.prioridade === 'média') {
                        priorityIcon = '<i class="fas fa-exclamation-triangle" style="color: #ffb300;"></i>';
                    } else {
                        priorityIcon = '<i class="fas fa-info-circle" style="color: #43a047;"></i>';
                    }
                    
                    let tagsHTML = '';
                    if (ajuste.tags && ajuste.tags.length > 0) {
                        tagsHTML = `<div class="adjustment-tags">${ajuste.tags.map(tag => {
                            if (tag === 'IGMA') {
                                return `<span class="tag igma-tag"><i class="fas fa-cog"></i> ${tag}</span>`;
                            } else {
                                return `<span class="tag">${tag}</span>`;
                            }
                        }).join('')}</div>`;
                    }
                    
                    adjustmentsHTML += `
                        <div class="adjustment-details">
                            <h4>${priorityIcon} ${ajuste.tipo}</h4>
                            <p>${ajuste.descricao}</p>
                            <p><strong>Prioridade:</strong> ${ajuste.prioridade.toUpperCase()}</p>
                            ${tagsHTML}
                        </div>
                        <hr style="margin: 15px 0; border: none; border-top: 1px dashed #ddd;">
                    `;
                });
                // Remove o último hr
                adjustmentsHTML = adjustmentsHTML.replace(/<hr[^>]*>$/, '');
            } else {
                adjustmentsHTML = '<div class="no-adjustments"><i class="fas fa-check-circle" style="font-size: 2rem; margin-bottom: 10px; color: #2ecc71;"></i><p>Não há ajustes pendentes para este termo.</p></div>';
            }
            
            modalBody.innerHTML = `
                <div style="display: flex; gap: 20px; margin-bottom: 20px;">
                    <div style="flex: 1;">
                        <p><strong>Categoria:</strong></p>
                        <span class="adjustment-category ${categoryBadgeClass}">${item.categoria}</span>
                    </div>
                    <div style="flex: 1;">
                        <p><strong>Status:</strong></p>
                        <span class="status ${statusClass}">${item.status}</span>
                    </div>
                </div>
                <div style="margin-top: 20px;">
                    <h3><i class="fas fa-clipboard-list"></i> Ajustes Pendentes</h3>
                    ${adjustmentsHTML}
                </div>
            `;
            
            termModal.style.display = 'flex';
        }

        // Função para fechar o modal
        function closeModal() {
            termModal.style.display = 'none';
        }

        // Função para exportar relatório
        function exportReport() {
            const categoryValue = categoryFilter.value;
            const statusValue = statusFilter.value;
            const searchValue = searchTerm.value.toLowerCase();
            
            const filteredData = tableData.filter(item => {
                const categoryMatch = categoryValue === '' || item.categoria === categoryValue;
                const statusMatch = statusValue === '' || item.status === statusValue;
                const searchMatch = item.termo.toLowerCase().includes(searchValue) || 
                                   item.categoria.toLowerCase().includes(searchValue);
                
                return categoryMatch && statusMatch && searchMatch;
            });
            
            let csvContent = "Categoria;Termo;Status;Ajustes Pendentes\n";
            
            filteredData.forEach(item => {
                const row = [
                    item.categoria,
                    item.termo,
                    item.status,
                    item.ajustes.length
                ].join(";");
                
                csvContent += row + "\n";
            });
            
            const blob = new Blob([csvContent], { type: 'text/csv;charset=utf-8;' });
            const url = URL.createObjectURL(blob);
            const link = document.createElement("a");
            link.setAttribute("href", url);
            link.setAttribute("download", "relatorio_termos.csv");
            link.style.visibility = 'hidden';
            document.body.appendChild(link);
            link.click();
            document.body.removeChild(link);
            
            // Mostrar mensagem de sucesso
            alert("Relatório exportado com sucesso!");
        }

        // Adicionar event listeners
        categoryFilter.addEventListener('change', filterData);
        statusFilter.addEventListener('change', filterData);
        searchTerm.addEventListener('input', filterData);
        closeModalBtn.addEventListener('click', closeModal);
        closeModalX.addEventListener('click', closeModal);
        exportBtn.addEventListener('click', exportReport);
        
        // Fechar modal ao clicar fora dele
        window.addEventListener('click', (event) => {
            if (event.target === termModal) {
                closeModal();
            }
        });

        // Inicializar a tabela
        renderTable(tableData);
    </script>
</body>
</html>
