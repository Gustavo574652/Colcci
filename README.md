-- Script Local ou de Servidor dependendo do sistema do jogo
-- BLUE LOCK - Sistema de Giros de Estilo (Gacha) - 172 Spins

-- Criação da Tabela de Estilos
local estilosDisponiveis = {
    "Velocista", "Técnico", "Atacante", "Defensivo", "Driblador", 
    "Finalizador", "Maestro", "Criador de Jogadas", "Resistente", "Ágil"
}

-- Função para gerar um estilo aleatório
local function girarEstilo()
    local indice = math.random(1, #estilosDisponiveis)
    return estilosDisponiveis[indice]
end

-- Dar 172 giros ao jogador
local function darGiros(jogador, quantidade)
    if not jogador then return end

    -- Criação de uma pasta de dados, se não existir
    local dados = jogador:FindFirstChild("Dados")
    if not dados then
        dados = Instance.new("Folder", jogador)
        dados.Name = "Dados"
    end

    -- Adiciona um valor para armazenar os estilos obtidos
    local estilos = dados:FindFirstChild("EstilosObtidos")
    if not estilos then
        estilos = Instance.new("Folder", dados)
        estilos.Name = "EstilosObtidos"
    end

    for i = 1, quantidade do
        local estiloGanho = girarEstilo()
