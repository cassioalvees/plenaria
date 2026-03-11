import React, { useState } from 'react';
import { 
  Monitor, Settings, Radio, FileText, AlignLeft, Users, 
  Palette, Play, X, RefreshCw, Upload, Plus, LayoutGrid, AlertCircle
} from 'lucide-react';

export default function App() {
  // Estados Globais
  const [themeColor, setThemeColor] = useState('bg-red-600');
  const [camaraName, setCamaraName] = useState('Câmara Municipal');
  const [sessionTitle, setSessionTitle] = useState('SESSÃO ORDINÁRIA');
  const [sessionSubtitle, setSessionSubtitle] = useState('');
  const [isLive, setIsLive] = useState(false);
  
  // Toggles de Transmissão
  const [toggles, setToggles] = useState({
    barra: true,
    projeto: true,
    ticker: true
  });

  // Texto do Projeto
  const [projetoText, setProjetoText] = useState('Teste de texto Teste de texto Teste de texto\nTeste de texto Teste de texto Teste de texto');

  // Tickers
  const [tickers, setTickers] = useState([
    'INSTAGRAM @CAMARAMUNICIPAL',
    'FACEBOOK /CAMARAMUNICIPAL',
    'YOUTUBE CÂMARA MUNICIPAL',
    'SITE WWW.CAMARA.CE.LEG.BR'
  ]);

  // Identificação (Vereadores)
  const [vereadores, setVereadores] = useState([
    { id: 1, name: 'TESTE', role: 'VEREADOR - PSD', active: true },
    { id: 2, name: '(vazio)', role: '', active: false },
    { id: 3, name: '(vazio)', role: '', active: false },
    { id: 4, name: '(vazio)', role: '', active: false },
    { id: 5, name: '(vazio)', role: '', active: false },
  ]);

  const cores = [
    { nome: 'Vermelho Clássico', classe: 'bg-red-600' },
    { nome: 'Azul Institucional', classe: 'bg-blue-600' },
    { nome: 'Verde Institucional', classe: 'bg-green-600' },
    { nome: 'Azul Celeste', classe: 'bg-sky-500' },
    { nome: 'Roxo Real', classe: 'bg-purple-600' },
    { nome: 'Dourado Premium', classe: 'bg-yellow-500' },
    { nome: 'Laranja Vibrante', classe: 'bg-orange-500' },
    { nome: 'Cinza Titânio', classe: 'bg-gray-500' },
  ];

  const handleToggle = (key) => {
    setToggles(prev => ({ ...prev, [key]: !prev[key] }));
  };

  return (
    <div className="min-h-screen bg-[#121212] text-gray-300 font-sans p-4 select-none">
      
      {/* Header Principal */}
      <header className="flex items-center justify-between mb-6 pb-4 border-b border-gray-800">
        <div className="flex items-center space-x-3">
          <div className="bg-red-600 text-white font-bold p-2 rounded">PP</div>
          <div>
            <h1 className="text-xl font-black text-white tracking-wider">PLENÁRIOPLAY</h1>
            <p className="text-xs text-gray-500">SISTEMA DE OVERLAY - CÂMARAS MUNICIPAIS</p>
          </div>
        </div>
        
        <div className="flex space-x-2">
          <Button icon={<LayoutGrid size={16} />} text="REORGANIZAR" />
          <Button icon={<Monitor size={16} />} text="OVERLAY" />
          <Button icon={<Play size={16} />} text="MOSTRAR TUDO" />
          <Button icon={<X size={16} />} text="LIMPAR TELA" className="bg-red-950 text-red-500 border-red-900" />
          <Button icon={<RefreshCw size={16} />} text="RESET" />
        </div>
      </header>

      {/* Grid Principal - 4 Colunas */}
      <div className="grid grid-cols-1 md:grid-cols-2 xl:grid-cols-4 gap-4">
        
        {/* COLUNA 1 */}
        <div className="space-y-4">
          
          <Panel title="CÂMARA MUNICIPAL" icon={<AlertCircle size={14} />}>
            <div className="space-y-4">
              <div>
                <label className="text-[10px] text-gray-500 mb-1 block">NOME DA CÂMARA</label>
                <input 
                  type="text" 
                  value={camaraName}
                  onChange={(e) => setCamaraName(e.target.value)}
                  className="w-full bg-[#1e1e1e] border border-gray-700 rounded p-2 text-sm text-white focus:outline-none focus:border-gray-500"
                />
              </div>
              <div>
                <label className="text-[10px] text-gray-500 mb-1 block">LOGOTIPO</label>
                <div className="border-2 border-dashed border-gray-700 rounded-lg p-6 flex flex-col items-center justify-center text-center cursor-pointer hover:border-gray-500 transition-colors">
                  <Upload size={24} className="text-red-600 mb-2" />
                  <span className="text-xs text-red-500 font-semibold">Clique ou arraste</span>
                </div>
              </div>
            </div>
          </Panel>

          <Panel title="TRANSMISSÃO" icon={<Radio size={14} />}>
            <div className="space-y-4">
              <div className="flex justify-between items-center">
                <span className="text-xs font-semibold">MODO</span>
              </div>
              <div className="flex space-x-2 bg-[#1e1e1e] p-1 rounded border border-gray-800">
                <button 
                  onClick={() => setIsLive(true)}
                  className={`flex-1 py-1 text-xs font-bold rounded flex items-center justify-center ${isLive ? 'bg-red-600 text-white' : 'text-gray-500 hover:text-white'}`}
                >
                  <div className={`w-2 h-2 rounded-full mr-2 ${isLive ? 'bg-white' : 'bg-gray-600'}`}></div>
                  AO VIVO
                </button>
                <button 
                  onClick={() => setIsLive(false)}
                  className={`flex-1 py-1 text-xs font-bold rounded flex items-center justify-center ${!isLive ? 'bg-blue-600 text-white' : 'text-gray-500 hover:text-white'}`}
                >
                  REPRISE
                </button>
              </div>

              <div className="space-y-3 pt-2">
                <ToggleRow label="Barra da sessão" active={toggles.barra} onClick={() => handleToggle('barra')} />
                <ToggleRow label="Projeto em votação" active={toggles.projeto} onClick={() => handleToggle('projeto')} />
                <ToggleRow label="Ticker / Rodapé" active={toggles.ticker} onClick={() => handleToggle('ticker')} />
              </div>
            </div>
          </Panel>

          <Panel title="OBS - ATALHOS" icon={<Settings size={14} />}>
            <div className="space-y-4">
              <div>
                <label className="text-[10px] text-gray-500 mb-1 block">BROWSER SOURCE - OBS STUDIO</label>
                <input 
                  type="text" 
                  readOnly 
                  value="http://localhost:3000/overlay.html" 
                  className="w-full bg-[#1e1e1e] border border-gray-800 rounded p-2 text-xs text-gray-400"
                />
              </div>
              <div className="text-[10px] text-gray-500 flex flex-col gap-1">
                <div className="flex justify-between"><span>Ctrl+Enter</span> <span className="text-gray-400">Mostrar tudo</span></div>
                <div className="flex justify-between"><span>Ctrl+Del</span> <span className="text-gray-400">Limpar tela</span></div>
                <div className="flex justify-between"><span>Esc</span> <span className="text-gray-400">Fechar modal</span></div>
              </div>
            </div>
          </Panel>

        </div>

        {/* COLUNA 2 */}
        <div className="space-y-4">
          
          <Panel title="SESSÃO" icon={<FileText size={14} />}>
            <div className="space-y-3">
              <div>
                <label className="text-[10px] text-gray-500 mb-1 block">TÍTULO - BARRA VERMELHA</label>
                <input 
                  type="text" 
                  value={sessionTitle}
                  onChange={(e) => setSessionTitle(e.target.value)}
                  className="w-full bg-[#1e1e1e] border border-gray-800 rounded p-2 text-sm text-white focus:border-gray-500 focus:outline-none uppercase font-bold"
                />
              </div>
              <div>
                <label className="text-[10px] text-gray-500 mb-1 block">SUBTÍTULO (OPCIONAL)</label>
                <input 
                  type="text" 
                  value={sessionSubtitle}
                  onChange={(e) => setSessionSubtitle(e.target.value)}
                  className="w-full bg-[#1e1e1e] border border-gray-800 rounded p-2 text-sm text-white focus:border-gray-500 focus:outline-none"
                />
              </div>
              <div>
                <label className="text-[10px] text-gray-500 mb-1 block">FAIXA ESCURA</label>
                <input 
                  type="text" 
                  value="ATIVIDADES LEGISLATIVAS"
                  readOnly
                  className="w-full bg-[#1e1e1e] border border-gray-800 rounded p-2 text-sm text-gray-400"
                />
              </div>
              
              <div>
                <label className="text-[10px] text-gray-500 mb-2 block">PRESETS</label>
                <div className="grid grid-cols-2 gap-2">
                  {['ORDINÁRIA', 'EXTRAORDINÁRIA', 'AUDIÊNCIA PÚBLICA', 'ITINERANTE', 'PRESTAÇÃO DE CONTAS', 'SESSÃO SOLENE'].map(preset => (
                    <button key={preset} onClick={() => setSessionTitle(`SESSÃO ${preset}`)} className="bg-[#1e1e1e] border border-gray-800 hover:border-gray-600 text-xs py-1.5 rounded transition-colors text-gray-400 hover:text-white">
                      {preset}
                    </button>
                  ))}
                </div>
              </div>
            </div>
          </Panel>

          <Panel title="PROJETO EM VOTAÇÃO" icon={<FileText size={14} />}>
            <div>
              <label className="text-[10px] text-gray-500 mb-1 block">TEXTO (EXIBE ATÉ 4 LINHAS NO OVERLAY)</label>
              <textarea 
                rows={5}
                value={projetoText}
                onChange={(e) => setProjetoText(e.target.value)}
                className="w-full bg-[#1e1e1e] border border-gray-800 rounded p-2 text-sm text-gray-300 focus:border-gray-500 focus:outline-none resize-none leading-tight"
              />
            </div>
          </Panel>

          <Panel title="TICKER / RODAPÉ" icon={<AlignLeft size={14} />}>
            <div className="space-y-2">
              <label className="text-[10px] text-gray-500 block">ITENS</label>
              {tickers.map((ticker, idx) => (
                <div key={idx} className="flex bg-[#1e1e1e] border border-gray-800 rounded overflow-hidden">
                  <div className="flex-1 p-2 text-xs text-gray-300">{ticker}</div>
                  <button className="bg-red-900/20 text-red-500 hover:bg-red-900/40 px-3 flex items-center justify-center border-l border-gray-800">
                    <X size={14} />
                  </button>
                </div>
              ))}
              <button className="w-full py-2 text-xs text-gray-400 hover:text-white border border-dashed border-gray-700 rounded flex items-center justify-center mt-2 hover:border-gray-500 transition-colors">
                <Plus size={14} className="mr-1" /> ADICIONAR ITEM
              </button>
            </div>
          </Panel>

        </div>

        {/* COLUNA 3 */}
        <div className="space-y-4">
          <Panel title="TARJA - IDENTIFICAÇÃO" icon={<Users size={14} />} fullHeight>
            
            <div className="flex border-b border-gray-800 mb-4">
              <button className="px-4 py-2 text-xs font-bold text-white border-b-2 border-red-600">VEREADORES</button>
              <button className="px-4 py-2 text-xs font-bold text-gray-500 hover:text-white transition-colors">PRESIDENTE</button>
              <button className="px-4 py-2 text-xs font-bold text-gray-500 hover:text-white transition-colors">TRIBUNA</button>
            </div>

            <div className="flex justify-between items-center mb-4">
              <span className="text-xs text-gray-500">30 CADASTRADOS</span>
              <button className="bg-red-600 text-white text-[10px] font-bold px-2 py-1 rounded flex items-center">
                <Plus size={12} className="mr-1" /> NOVO
              </button>
            </div>

            <div className="space-y-2 overflow-y-auto max-h-[600px] pr-2 custom-scrollbar">
              {vereadores.map((ver, idx) => (
                <div key={idx} className={`flex items-center p-2 rounded border ${ver.active ? 'border-red-900 bg-red-950/20' : 'border-gray-800 bg-[#1e1e1e]'}`}>
                  <div className="w-6 text-xs text-gray-600 font-mono text-center">{ver.id}</div>
                  <div className="flex-1 ml-2">
                    <div className={`text-sm font-bold ${ver.active ? 'text-white' : 'text-gray-400'}`}>{ver.name}</div>
                    {ver.role && <div className="text-[10px] text-gray-500 uppercase">{ver.role}</div>}
                  </div>
                  <div className="flex space-x-1 items-center">
                    {ver.name !== '(vazio)' && (
                      <div className="flex bg-[#121212] rounded p-0.5 border border-gray-800">
                        <button className={`px-2 py-1 text-[10px] font-bold rounded ${ver.active ? 'bg-red-600 text-white' : 'text-gray-500'}`}>ON</button>
                        <button className={`px-2 py-1 text-[10px] font-bold rounded ${!ver.active ? 'bg-gray-700 text-white' : 'text-gray-500'}`}>OFF</button>
                      </div>
                    )}
                    <button className="p-1.5 text-red-500 hover:bg-red-900/30 rounded ml-1">
                      <X size={14} />
                    </button>
                  </div>
                </div>
              ))}
              
              {/* Mock adicionais para visual */}
              {[6,7,8,9,10,11,12].map(num => (
                 <div key={num} className="flex items-center p-2 rounded border border-gray-800 bg-[#1e1e1e]">
                 <div className="w-6 text-xs text-gray-600 font-mono text-center">{num}</div>
                 <div className="flex-1 ml-2 text-sm text-gray-600 italic">(vazio)</div>
                 <button className="p-1.5 text-red-900/50 rounded ml-1 cursor-not-allowed">
                   <X size={14} />
                 </button>
               </div>
              ))}
            </div>
          </Panel>
        </div>

        {/* COLUNA 4 */}
        <div className="space-y-4">
          
          <Panel title="PREVIEW - 1920x1080" icon={<Monitor size={14} />}>
            <div className="aspect-video bg-black rounded border border-gray-800 relative overflow-hidden flex flex-col justify-between p-2 mb-4">
               {/* Simulação do Overlay no Preview */}
               
               {/* Logo Top Left */}
               <div className="w-16 h-10 bg-[#1a1a1a] border border-gray-800 flex items-center justify-center text-[8px] text-gray-600">LOGO</div>

               {/* Identificação Simulação */}
               <div className="absolute top-10 left-2 opacity-80">
                  <div className={`text-[8px] text-white ${themeColor} px-2 py-0.5 inline-block font-bold`}>VEREADOR</div>
                  <div className="bg-white text-black text-[10px] px-2 font-bold min-w-[100px]">TESTE PSD</div>
               </div>

               {/* Rodapé Simulação */}
               <div className="mt-auto w-full">
                  <div className="flex justify-between items-end text-[6px] text-white px-2 mb-1">
                    <span className="uppercase">{camaraName}</span>
                    <span className="text-right">10 FEV<br/>10:15:20</span>
                  </div>
                  {toggles.barra && (
                    <div className={`w-full ${themeColor} h-4 flex items-center px-2 text-[8px] text-white font-bold uppercase`}>
                      {sessionTitle}
                    </div>
                  )}
                  {toggles.ticker && (
                    <div className="w-full bg-white h-3 flex items-center px-2 text-[6px] text-black overflow-hidden font-bold">
                      {tickers[0]} &bull; {tickers[1]}
                    </div>
                  )}
               </div>
            </div>

            <button className={`w-full py-2 ${themeColor} text-white font-bold rounded text-sm mb-2 flex justify-center items-center hover:opacity-90 transition-opacity`}>
              <Play size={16} className="mr-2" /> MOSTRAR TUDO
            </button>
            <button className="w-full py-2 bg-[#1e1e1e] border border-gray-800 text-gray-400 font-bold rounded text-sm flex justify-center items-center hover:bg-gray-800 transition-colors">
              <X size={16} className="mr-2" /> LIMPAR
            </button>
          </Panel>

          <Panel title="TEMAS DE CORES" icon={<Palette size={14} />}>
            <div className="grid grid-cols-2 gap-2">
              {cores.map((cor, idx) => (
                <button 
                  key={idx} 
                  onClick={() => setThemeColor(cor.classe)}
                  className={`flex items-center p-2 rounded border text-xs transition-colors ${themeColor === cor.classe ? 'border-gray-400 bg-gray-800' : 'border-gray-800 bg-[#1e1e1e] hover:border-gray-600'}`}
                >
                  <div className={`w-3 h-3 rounded-full mr-2 ${cor.classe}`}></div>
                  <span className={themeColor === cor.classe ? 'text-white font-bold' : 'text-gray-400'}>{cor.nome}</span>
                </button>
              ))}
            </div>
          </Panel>

        </div>

      </div>
    </div>
  );
}

// Componentes Auxiliares
const Panel = ({ title, icon, children, fullHeight }) => (
  <div className={`bg-[#181818] border border-gray-800 rounded-lg p-4 shadow-xl ${fullHeight ? 'h-full' : ''}`}>
    <div className="flex items-center text-gray-400 font-bold text-xs tracking-wider mb-4 border-b border-gray-800 pb-2">
      <span className="mr-2">{icon}</span>
      {title}
    </div>
    {children}
  </div>
);

const Button = ({ icon, text, className }) => (
  <button className={`flex items-center px-3 py-1.5 text-xs font-semibold rounded border border-gray-700 bg-[#1e1e1e] text-gray-300 hover:bg-gray-700 hover:text-white transition-colors ${className || ''}`}>
    <span className="mr-1.5 opacity-80">{icon}</span>
    {text}
  </button>
);

const ToggleRow = ({ label, active, onClick }) => (
  <div className="flex justify-between items-center bg-[#1e1e1e] border border-gray-800 rounded px-3 py-2">
    <span className="text-xs text-gray-300">{label}</span>
    <button 
      onClick={onClick}
      className={`w-10 h-5 rounded-full relative transition-colors ${active ? 'bg-green-600' : 'bg-gray-700'}`}
    >
      <div className={`absolute top-0.5 left-0.5 w-4 h-4 rounded-full bg-white transition-transform ${active ? 'translate-x-5' : 'translate-x-0'}`}></div>
    </button>
  </div>
);
