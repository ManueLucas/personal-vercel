<script>
    import ProjectCard from "./ProjectCard.svelte";
    import SKLearnIcon from "../lib/images//2560px-Scikit_learn_logo_small.svg.png";
    import FlaskIcon from "../lib/images//flask-svgrepo-com.svg";
    import BootstrapIcon from "../lib/images//bootstrap-svgrepo-com.svg";
    import CPPIcon from "../lib/images//cpp-svgrepo-com.svg";
    import CSSIcon from "../lib/images//css-3-svgrepo-com.svg";
    import HTMLIcon from "../lib/images//html-5-svgrepo-com.svg";
    import JSIcon from "../lib/images//javascript-logo-svgrepo-com.svg";
    import PythonIcon from "../lib/images//python-svgrepo-com.svg";
    import PytorchIcon from "../lib/images//pytorch-svgrepo-com.svg";
    import QTIcon from "../lib/images//qt-svgrepo-com.svg";
    import ReactIcon from "../lib/images//react-svgrepo-com.svg";
    import SQLIcon from "../lib/images//sql-svgrepo-com.svg";
    import WebpackIcon from "../lib/images//webpack-svgrepo-com.svg";
    import TensorFlowIcon from "../lib/images//tensorflow-svgrepo-com.svg";
    import ThreeJSIcon from "../lib/images//Three.js_Icon.svg.png";

    import DepthSquaredScreenshot from "../lib/images//DepthSquaredSS1.png";
    import DepthSquaredOutput from "../lib/images//DepthSquaredSS2.png";

    import MNISTFigure1 from "../lib/images//misclass.png";
    import MNISTFigure2 from "../lib/images//RNN_err.png";
    import MNISTFigure3 from "../lib/images//LSTMParams.png";

    import AEDSS1 from "../lib/images//AEDSS1.png";
    import AEDSS2 from "../lib/images//AEDSS2.png";
    import AEDSS3 from "../lib/images//AEDSS3.png";

    import ChromaVisionSS1 from "../lib/images//ChromaVisionSS1.png";

    let projectDataTemplate = [
        {
            name: "DepthSquared",
            tools: [
                { name: "JavaScript", icon: JSIcon },
                { name: "TensorFlow", icon: TensorFlowIcon },
                { name: "Flask", icon: FlaskIcon },
                { name: "three.js", icon: ThreeJSIcon },
            ],
            images: [DepthSquaredScreenshot, DepthSquaredOutput],
            collaborators: "Gurtej Grewal, Saad Sheikh, Hamza Alsarakbi",
            description: `Hackathon Submission - Proof-of-concept for a generative adversarial network powered app for 3D artists and game 
            developers to generate normal, displacement, and roughness maps for texturing 3D assets. <br/><br/>
            Users can preview the texture generated using the app after generating the map, and can decide to regenerate or download the files.`,
        },
        {
            name: "ChromaVision",
            tools: [
                { name: "JavaScript", icon: JSIcon },
                { name: "HTML", icon: HTMLIcon },
                { name: "CSS", icon: CSSIcon },
            ],
            images: [ChromaVisionSS1],
            collaborators: "Gurtej Grewal, Saad Sheikh",
            description: `Hackthon Submission - A mobile and desktop accessibility app for severely achromatopsic and 
            visually impaired people to navigate color in the world around them.<br/><br/>
            Connects to an external color-matching API and uses the device camera as an eyedropper tool for the world.`,
        },
        {
            name: "MNIST Digit Predictor",
            tools: [
                { name: "PyTorch", icon: PytorchIcon },
                { name: "Python", icon: PythonIcon },
                { name: "SKLearn", icon: SKLearnIcon },
            ],
            images: [MNISTFigure3, MNISTFigure1, MNISTFigure2],
            collaborators: "Riley Olson",
            description: `Academic Assignment - Jupyter notebook in Google Colab, implementing a 
            Long-Term Short-Memory neural network to predict the integer value from handwritten numbers.<br/><br/>
            Other data science techniques employed to analyze the training dataset given: <br/>HDBScan, t-SNe and UMAP to
            determine class separability, ADASyn for addressing class imbalances, PCA and LDA for dimensionality reduction.`,
        },
        {
            name: "AED Simulator",
            tools: [
                { name: "Qt", icon: QTIcon },
                { name: "C++", icon: CPPIcon },
                { name: "Python", icon: PythonIcon },
                { name: "SKLearn", icon: SKLearnIcon },
            ],
            images: [AEDSS1, AEDSS2, AEDSS3],
            collaborators: "Gurtej Grewal, Boris Zugic, Libeamlak Kiros",
            description: `Academic Assignment - A C++ program made in the Qt framework simulating the real-life conditions
             of operating a semi-automatic defibrillation machine, complete with audio and interface based off a Zoll product.<br/><br/>
             Also features a semi-realistic EKG reading based on the state of the patient, generating noisy signals using
             fourier analysis of real ECG data using SKLearn in python.`,
        },
    ];
</script>

<div class="project-section col">
    {#each projectDataTemplate as projectData, idx}
        <ProjectCard {...projectData} index={idx} />
    {/each}
</div>

<style>
    .project-section {
        height: 100vh;
        position: absolute;
        left: -60%;
        width: 100%;
        opacity: 90%;
        overflow-y: auto; /* Allow vertical scrolling */
    }
</style>
