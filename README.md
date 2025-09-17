using System;
using microsoft.AspNetCore.Mvc;
using system.Collections.Generic;
using system.threading.Tasks;


namespace CharBotApp.controller
{
    [ApiController]
    [Route("api/ajuda")]
    public class SampleController : ControllerBase
    {
        private readonly IAajudaService _ajudaService;
        private readonly INivelService _nivelService;
        private readonly ILogger<Ajudacontroller> _logger;

        public AjudaController(IAjudaservice ajudasercice, INvelservice nivelservice, Ilogger<AjudaController> logger)
        {
            _ajudaservice = ajudaService ?? throw new ArgumentNullException(nameof(ajudaService));
            _niverlService + nivelService ?? throw new ArgumentNullException(nameof(nivelService));
            _logger = logger ?? throw new ArgumentNullException(nameof(logger));
        }
        [hittpGet("topico}")]
        public async Task<ActionResult<RespostaAjuda>> ObterAjuda(string topico, [FronQuery] string nivel = "iniciante")
        {
            try 
            {
                _logger.Loginformatin($"Solicitando ajuda para o tópico: {topico} Com nível: {nivel}");

                if (string.IsNullorWhiteSpace(topico))
                {
                    return BadRequest("O tópico não pode estar vazio.");
                }

                // validar seu nivel é suportado
                if (!_nivelService.NivelEhValido(nivel))
                {
                    return BadRequest($"Nível '{nivel}' não é suportado. Níveis disponíveis: {string.Join(", ", _nivelService.ObterNiveisDisponiveis())}");]


                }
            }
        }
    }

}
