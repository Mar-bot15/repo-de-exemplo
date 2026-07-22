# repo-ex 4

print('Bem vindo a lista de contatos de Márcio Paiani Davila Junior')
print('-' * 60)
print('-' * 17 , 'Menu Principal', '-' * 27)
listaContatos = []
idGlobal = 4963173

def cadastrarContato(id_contato):
  nome = input('Informe o nome do contato: ')
  atividade = input('Informe a atividade do contato: ')
  telefone = input('Informe o numero do contato: ')

  contato = {'id': id_contato, 'nome': nome, 'atividade': atividade, 'telefone': telefone}

  listaContatos.append(contato.copy())
  print('Contato cadastrado com sucesso!')

def consultarContato():
  if not listaContatos:
    print('A lista de contatos está vazia.')
    return
  while True:
    print('-' * 17 , 'Menu de Consulta', '-' * 27)
    print('1. Consultar todos os contatos')
    print('2. Consultar contato por ID')
    print('3. Consultar por Atividade')
    print('4. Voltar ao Menu Principal') # Corrected menu option
    opc_consulta = input('Escolha uma opção: ')

    if opc_consulta == '4': # Corrected option
      return
    elif opc_consulta == '1':
      if not listaContatos:
        print('A lista de contatos está vazia.')
      else:
        for contato in listaContatos:
          for chave, valor in contato.items():
            print(f'{chave}: {valor}')
          print('-' * 30)
    elif opc_consulta == '2':
      try:
        idInformado = int(input('Informe o ID do contato: '))
        encontrado = False
        for contato in listaContatos:
          if contato['id'] == idInformado:
            for chave, valor in contato.items():
              print(f'{chave}: {valor}')
            print('-' * 30)
            encontrado = True
            break
        if not encontrado: # Correctly indented, associated with opc_consulta == '2'
          print('Contato não encontrado.')
      except ValueError:
        print('ID inválido. Por favor, digite um número inteiro.')
    elif opc_consulta == '3': # Indentation corrected, this is a new elif block
        atividadeInformada = input('Informe a atividade do contato: ')
        encontrado = False
        for contato in listaContatos:
            if contato['atividade'].upper() == atividadeInformada.upper():
                for chave, valor in contato.items():
                    print(f'{chave}: {valor}')
                print('-' * 30)
                encontrado = True
        if not encontrado:
            print('Nenhum contato encontrado com essa atividade.')
    else:
      print('Opção inválida, tente novamente.')

def removerContato():
  if not listaContatos:
    print('A lista de contatos está vazia. Não há contatos para remover.')
    return
  while True:
    try:
      idInformado = int(input('Informe o ID do contato a ser removido: '))
      encontrado = False
      for contato in listaContatos:
        if contato['id'] == idInformado:
          listaContatos.remove(contato)
          print('Contato removido com sucesso!')
          encontrado = True
          break
      if not encontrado:
        print('Contato não encontrado.')
      return
    except ValueError:
      print('ID inválido. Por favor, digite um número inteiro.')
    except Exception as e:
      print(f'Ocorreu um erro inesperado: {e}. Tente novamente.')

# Codigo principal

while True:
  print('1. Cadastrar Contato')
  print('2. Consultar Contato(s)')
  print('3. Remover Contato')
  print('4. Sair')
  opc = input('Escolha uma opção: ')

  if opc == '1':
    cadastrarContato(idGlobal)
    idGlobal += 1

  elif opc == '2':
    consultarContato()

  elif opc == '3':
    removerContato()

  elif opc == '4':
    print('Encerrando o programa. Obrigado por usar!')
    break
  else:
    print('Opção inválida, tente novamente.')
