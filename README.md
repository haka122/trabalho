class Tarefa:
    def __init__(self, nome):
        self.nome = nome
        self.concluida = False
        self.proxima = None

class ListaDeTarefas:
    def __init__(self):
        self.inicio = None

    def adicionar_tarefa(self, nome):
        nova = Tarefa(nome)
        nova.proxima = self.inicio
        self.inicio = nova

    def remover_tarefa(self, nome):
        atual = self.inicio
        anterior = None
        while atual:
            if atual.nome == nome:
                if anterior:
                    anterior.proxima = atual.proxima
                else:
                    self.inicio = atual.proxima
                print(f"Tarefa '{nome}' removida.")
                return
            anterior = atual
            atual = atual.proxima
        print(f"Tarefa '{nome}' não encontrada.")

    def marcar_concluida(self, nome):
        atual = self.inicio
        while atual:
            if atual.nome == nome:
                atual.concluida = True
                print(f"Tarefa '{nome}' marcada como concluída.")
                return
            atual = atual.proxima
        print(f"Tarefa '{nome}' não encontrada.")

    def listar_tarefas(self):
        atual = self.inicio
        if not atual:
            print("Nenhuma tarefa cadastrada.")
            return
        while atual:
            status = "Concluída" if atual.concluida else "Pendente"
            print(f"- {atual.nome} [{status}]")
            atual = atual.proxima

    def buscar_tarefa(self, nome):
        atual = self.inicio
        while atual:
            if atual.nome == nome:
                status = "Concluída" if atual.concluida else "Pendente"
                print(f"Tarefa encontrada: {nome} [{status}]")
                return
            atual = atual.proxima
        print(f"Tarefa '{nome}' não encontrada.")
