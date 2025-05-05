# desafio-finceiro
import { useState } from "react";
import { Card, CardContent } from "@/components/ui/card";
import { Textarea } from "@/components/ui/textarea";
import { Checkbox } from "@/components/ui/checkbox";
import { Progress } from "@/components/ui/progress";

const desafios = [
  "Anota tudo que ganha",
  "Anota tudo que gasta",
  "Separa fixos e variáveis",
  "Vê onde pode cortar",
  "Define teu 'porquê'",
  "Instala app ou faz caderno de controle",
  "Faz uma revisão da semana",
  "Cancela 1 gasto inútil",
  "Tira o cartão da mão (ou congela)",
  "Passa 1 dia sem gastar nada",
  "Faz uma lista de dívidas (se tiver)",
  "Cria plano de pagamento",
  "Pensa num plano pra renda extra",
  "Descansa e se recompensa sem gastar",
  "Define um valor fixo pra guardar",
  "Cria 'cofre digital' ou separado",
  "Compra consciente: precisa ou só quer?",
  "Prepara 1 refeição em casa",
  "Separa tempo pra aprender sobre finanças",
  "Ajusta tuas metas",
  "Faz uma pausa e celebra a jornada",
  "Monta orçamento do próximo mês",
  "Define meta de reserva de emergência",
  "Pesquisa uma forma segura de investir",
  "Revisa se pode aumentar a economia mensal",
  "Planeja compras maiores (curto prazo)",
  "Visualiza tua vida com mais controle",
  "Cria um 'kit emergência'",
  "Faz resumo de tudo que aprendeu",
  "Se banca: você tá no controle agora"
];

export default function DesafioFinanceiro() {
  const [checklist, setChecklist] = useState(Array(desafios.length).fill(false));
  const [notas, setNotas] = useState(Array(desafios.length).fill(""));

  const toggleCheck = (index) => {
    const novaLista = [...checklist];
    novaLista[index] = !novaLista[index];
    setChecklist(novaLista);
  };

  const handleNota = (index, value) => {
    const novasNotas = [...notas];
    novasNotas[index] = value;
    setNotas(novasNotas);
  };

  const progresso = (checklist.filter(Boolean).length / desafios.length) * 100;

  return (
    <div className="bg-black text-white min-h-screen p-6">
      <h1 className="text-2xl font-bold mb-4">Desafio Financeiro – 30 Dias</h1>
      <Progress value={progresso} className="mb-6" />
      <div className="grid gap-4">
        {desafios.map((titulo, i) => (
          <Card key={i} className="bg-gray-900 border border-gray-700">
            <CardContent className="flex flex-col space-y-2 p-4">
              <div className="flex items-center space-x-2">
                <Checkbox checked={checklist[i]} onCheckedChange={() => toggleCheck(i)} />
                <span className={checklist[i] ? "line-through" : ""}>Dia {i + 1}: {titulo}</span>
              </div>
              <Textarea
                placeholder="Anotações do dia..."
                value={notas[i]}
                onChange={(e) => handleNota(i, e.target.value)}
                className="bg-gray-800 text-white border-gray-600"
              />
            </CardContent>
          </Card>
        ))}
      </div>
    </div>
  );
}
