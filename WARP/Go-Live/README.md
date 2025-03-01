# Generate WAF Go-Live Report

The executive summary report presentation is generated by the following components:

- GenerateWAFReport.ps1
- PnP_PowerPointReport_Template.pptx
- WAF Category Descriptions.csv

# Prerequisites

- [PowerShell 7.3 or later](https://docs.microsoft.com/en-us/powershell/scripting/install/installing-powershell?view=powershell-7)
- PowerPoint
- CSV report exported from the [Well-Architected Go-Live Assessment](https://aka.ms/assessments) tool

>NOTE: PowerShell is a cross-platform task automation and configuration management framework from Microsoft. It is designed to automate repetitive tasks and simplify the management of complex systems. Windows PowerShell, on the other hand, is a specific version of PowerShell that is designed to work specifically with Windows operating systems. It includes additional features and capabilities that are specific to Windows, such as cmdlets for managing Active Directory, Windows Server, and other Windows-specific technologies.

# Running the script

This script uses [PowerShell 7.3 (cross-platform)](https://learn.microsoft.com/en-us/powershell/scripting/install/installing-powershell-on-windows?view=powershell-7.3#installing-the-msi-package) to create a customer presentation PowerPoint deck. To generate the presentation, follow these steps:

1. Run the GenerateWAFReport.ps1 script from the working directory where the script is located.
2. The script will prompt you to select the CSV report that was downloaded.
3. Wait for the execution to complete.
4. Locate the Executive Summary Report in the working directory with the current timestamp, e.g. PnP_PowerPointReport_Template_XXXX.PPTX.

>IMPORTANT: Make sure to use PowerShell instead of Windows PowerShell when running scripts to avoid encountering errors.

Following is detailed script documentation.

```
This script generates a customer presentation PowerPoint deck using a Well-Architected Go-Live Assessment Report CSV as input. The report must be located in the same directory as the following files: 
    - GenerateWAFReport.ps1
    - PnP_PowerPointReport_Template.pptx
    - WAF Category Descriptions.csv

INPUTS

This script requires a Well-Architected Assessment Report in CSV format as input.

OUTPUTS

The script will create a PowerPoint file in the current directory with a name in the following format: Azure Well-Architected $AssessmentType Review - Executive Summary - mmm-dd-yyyy hh.mm.ss.pptx.

PARAMETERS

AssessmentReport

The path to the Well-Architected Assessment Report should be in the following format:

-AssessmentReport: "./folder/file.csv"

EXAMPLE
 .\GenerateWAFReport.ps1 
        -AssessmentReport ".\Azure_Well_Architected_Go-Live_Review.csv" 

```

After generating the presentation, follow these steps:

- Check the presentation for errors.
- Add any additional context that is relevant to workload such as business purpose, scale, and customer non-functional requirements (availability / data residency/ regulatory concerns).
- Add any relevant screenshots from architecture artifacts or discovery through the Azure portal.

# Troubleshooting

On Windows systems it may happen that execution of PowerShell scripts is blocked by default and following error can occure:

```
File cannot be loaded because the execution of scripts is disabled on this system. Please see "get-help about_signing" for more details
```

To unblock the script, set the execution policy in PowerShell with following command:

```powershell
Set-ExecutionPolicy -ExecutionPolicy Unrestricted -Scope Process
```

This will set the execution policy to unrestricted for the current PowerShell session only. After closing PowerShell, execution policy will be set back to its previous value. For more information about PowerShell execution policies, see [about_Execution_Policies](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_execution_policies?view=powershell-7.1).

# License

Licensed under MIT. See [LICENSE](LICENSE) for more information.