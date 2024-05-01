# Aprenda-a-Criar-um-Sistema-de-Estacionamento-Usando-TypeScript

Desenvolvimento de um sistema de estacionamento usando TypeScript, explicando o tema e fornecendo uma descrição detalhada do projeto com exemplos práticos. Vamos dividir isso em módulos para facilitar o entendimento e a organização do código.

### Módulo 1: Introdução ao TypeScript e Configuração do Ambiente
**TypeScript** é um superset de JavaScript que adiciona tipagem estática ao idioma. Isso significa que você pode definir tipos para suas variáveis e funções, o que pode ajudar a prevenir muitos tipos de erros comuns em tempo de compilação, antes mesmo de seu código ser executado.

Para começar, você precisará instalar o Node.js e o npm (Node Package Manager). Depois, instale o TypeScript globalmente usando o npm:

```bash
npm install -g typescript
```

### Módulo 2: Estruturando o Projeto
Vamos estruturar nosso projeto em pastas e arquivos. Para um sistema de estacionamento, você pode ter uma estrutura de diretório como esta:

```
/estacionamento
    /src
        index.ts
        /modelos
            veiculo.ts
            estacionamento.ts
        /servicos
            estacionamentoServico.ts
    tsconfig.json
```

### Módulo 3: Definindo Modelos
Em `veiculo.ts`, você pode definir uma classe para veículos:

```typescript
export class Veiculo {
    constructor(public placa: string, public horaEntrada: Date) {}
}
```

Em `estacionamento.ts`, você pode definir uma classe para o estacionamento:

```typescript
import { Veiculo } from './veiculo';

export class Estacionamento {
    private veiculos: Veiculo[] = [];

    public adicionarVeiculo(veiculo: Veiculo): void {
        this.veiculos.push(veiculo);
    }

    // Outros métodos como removerVeiculo, calcularTempoEstacionado, etc.
}
```

### Módulo 4: Serviços e Lógica de Negócios
Em `estacionamentoServico.ts`, você implementará a lógica para gerenciar o estacionamento:

```typescript
import { Estacionamento } from '../modelos/estacionamento';
import { Veiculo } from '../modelos/veiculo';

export class EstacionamentoServico {
    private estacionamento = new Estacionamento();

    public entrarVeiculo(placa: string): void {
        const veiculo = new Veiculo(placa, new Date());
        this.estacionamento.adicionarVeiculo(veiculo);
    }

    // Outros métodos como sairVeiculo, calcularCobranca, etc.
}
```

### Módulo 5: Integrando e Testando
Finalmente, em `index.ts`, você integrará todos os módulos e testará o sistema:

```typescript
import { EstacionamentoServico } from './servicos/estacionamentoServico';

const estacionamentoServico = new EstacionamentoServico();

// Adiciona veículos ao estacionamento
estacionamentoServico.entrarVeiculo('ABC-1234');
// ...

// Testes e lógica adicional
```

Para compilar seu projeto TypeScript, use o comando `tsc` na raiz do projeto. Isso irá compilar seus arquivos `.ts` em `.js`, que podem ser executados em qualquer ambiente JavaScript.

Lembre-se, TypeScript é poderoso e pode realmente tornar seu desenvolvimento mais seguro e eficiente.
