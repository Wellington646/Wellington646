Função para filtrar funcionários por cargo
def filtrar_funcionarios_por_cargo(funcionarios, cargo):
"""
Filtra uma lista de funcionários pelo cargo especificado.

Args:
funcionarios (list): Lista de dicionários com informações dos funcionários.
cargo (str): Cargo a ser filtrado.

Returns:
list: Lista com os nomes dos funcionários que ocupam o cargo especificado.
"""
return [funcionario['nome'] for funcionario in funcionarios if funcionario['cargo'] == cargo]

Leitura de dados
n = int(input("Número de funcionários: "))
funcionarios = []
for i in range(n):
id = int(input(f"ID do funcionário {i+1}: "))
nome = input(f"Nome do funcionário {i+1}: ")
cargo = input(f"Cargo do funcionário {i+1}: ")
funcionarios.append({'id': id, 'nome': nome, 'cargo': cargo})

cargo_filtrar = input("Cargo para filtrar: ")

Chamada da função e impressão da saída
nomes_filtrados = filtrar_funcionarios_por_cargo(funcionarios, cargo_filtrar)
print(nomes_filtrados)

Exemplo de uso
funcionarios = [
{'id': 1, 'nome': 'Ana', 'cargo': 'Desenvolvedora'},
{'id': 2, 'nome': 'Pedro', 'cargo': 'Gerente'},
{'id': 3, 'nome': 'Maria', 'cargo': 'Desenvolvedora'}
]
cargo_filtrar = 'Desenvolvedora'
print(filtrar_funcionarios_por_cargo(funcionarios, cargo_filtrar))  # Saída: ['Ana', 'Maria']
