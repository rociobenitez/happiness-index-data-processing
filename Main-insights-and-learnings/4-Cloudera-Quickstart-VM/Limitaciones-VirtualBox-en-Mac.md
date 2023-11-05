# Limitaciones en la Instalación de VirtualBox en Mac M1

Si eres propietario de un MacBook Air con el procesador Apple M1 (Arm), es importante tener en cuenta que la instalación de VirtualBox en esta configuración puede presentar limitaciones significativas. VirtualBox es una aplicación diseñada principalmente para ejecutarse en procesadores Intel x86-64, lo que significa que no es nativamente compatible con la arquitectura Arm utilizada por los procesadores Apple M1.

Según la [documentación oficial de VirtualBox](https://www.virtualbox.org/manual/ch01.html#hostossupport), las limitaciones se especifican de la siguiente manera:

- **Supported Host Operating Systems**:
  VirtualBox es compatible con macOS, pero para las versiones 10.15 (Catalina), 11 (Big Sur), y 12 (Monterey) se requiere hardware Intel. Esto excluye a los dispositivos con procesadores Apple M1.
  
- **Installer Package for macOS/Arm64**:
  Existe un paquete de instalación disponible para macOS/Arm64 que está diseñado específicamente para sistemas con procesadores Apple silicon (M1). Sin embargo, este paquete está en una versión de "Desarrollo Preliminar" y representa un proyecto en curso. Además, el rendimiento es bastante modesto en comparación con la ejecución nativa.

Dado que VirtualBox no es una opción ideal para Mac M1 en este momento, es posible que desees considerar alternativas como la opción nativa de Apple, [Rosetta 2](https://support.apple.com/es-es/HT211861), [Parallels Desktop](https://www.parallels.com/es/) o [VMware Fusion](https://www.vmware.com/es/products/fusion.html), para ejecutar máquinas virtuales en tu Mac M1. Estas alternativas pueden ofrecer un mejor rendimiento y una experiencia de virtualización más fluida en sistemas basados en Apple M1.